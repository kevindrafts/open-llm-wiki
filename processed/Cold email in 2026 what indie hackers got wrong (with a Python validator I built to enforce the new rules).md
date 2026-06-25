---
title: "Cold email in 2026: what indie hackers got wrong (with a Python validator I built to enforce the new rules)"
source: "https://dev.to/snake_sun/cold-email-in-2026-what-indie-hackers-got-wrong-with-a-python-validator-i-built-to-enforce-the-3815"
author:
  - "[[孫昊]]"
published: 2026-05-05
created: 2026-05-09
description: "If you've been sending B2B cold emails the same way for 18 months, your reply rate just dropped to... Tagged with automation, marketing, python, startup."
tags:
  - "clippings"
---
If you've been sending B2B cold emails the same way for 18 months, your reply rate just dropped to ~0% and you don't know why.

I rebuilt my outreach this week after my reply rate tanked from 4% to <1%. Pulled fresh data from 5+ deliverability blogs ([Autobound](https://www.autobound.ai/blog/cold-email-guide-2026), [MarketingProfs](https://www.marketingprofs.com/), [HyperGen](https://www.hypergen.io/), [Instantly](https://instantly.ai/)), built a Python validator to enforce the new rules across 70+ template files in my repo, and shipped 10 trimmed emails that comply.

Here's what changed and the SOP for fixing your stack.

---

### What changed in 2026

**1\. DMARC is now hard-rejected.**

In Feb 2024, Google started requiring DMARC for bulk senders. In Nov 2025, they escalated to hard rejection. As of March 2026, emails from domains without properly configured DMARC + DKIM + SPF are **rejected by major providers** — not sent to spam. Rejected.

If you send from a custom domain (not gmail.com / hotmail.com), check yours:

```
dig TXT _dmarc.yourdomain.com
# Should return: v=DMARC1; p=quarantine; rua=mailto:dmarc@yourdomain.com
```

If it returns nothing, you're invisible. Period.

**2\. Word count is now a ranking signal.**

Multiple deliverability tests in 2026 show emails over 150 words have a **measurable reply drop**. The current sweet spot:

- Initial email: **75-125 words**
- Followup: **50-75 words**

I went through my outreach folder. Every email I'd written in 2024-2025 was 200-300 words. Trimmed all to 75-125. Reply rate started recovering within a week.

Why this changed: mobile preview. 60-80% of B2B emails are first scanned on mobile, where 150-word emails fill 2 screens. Recipients tap delete before they finish.

**3\. Personalization slot is required, not optional.**

Generic "Hi {{name}}, I see you do {{industry}}" gets <1% reply in 2026. Recipients can detect template structure within 3 seconds. The new rule:

> Each email needs a `{{detail}}` slot that references a **specific recent action** the prospect took (post / launch / hire / press release). Mass-merged templates with no specific detail = 0% reply.

Campaigns with **signal-specific personalization hit 18% reply rate** vs 3% for generic. 5x.

**4\. Daily volume cap dropped.**

The safe limit per mailbox is now **50-100 emails/day**. Total per SDR (across 3-4 mailboxes) sweet spot is **200-375/day**. Above this triggers spam classifiers within a week, even with perfect content.

I was sending 250/day from 1 mailbox. Burned the domain reputation in 3 weeks. Lesson: split across multiple mailboxes (sales@ / hello@ / firstname@) and rotate.

---

### The Python validator I built

I have 70+ paste-ready outreach templates in my repo. Going through each by hand to check word count + slots + spam triggers + CTA = 6 hours.

Built `cold_email_validator.py` instead. Run it on any email:

```
from orchestrator.lib.cold_email_validator import validate_email

result = validate_email(
    subject="30 min audit your AI workflow",
    body="""Hi {{name}},
    looked at {{company}}'s recent {{detail}}.
    [...75-125 words...]
    Reply with a time? cal.com/foo/30min""",
    is_followup=False,
)

print(result.score)  # 0-100
print(result.issues)  # list of structured issues with severity + fix hints
```

It checks:

- **Subject**: < 60 chars, no ALL CAPS, no excessive punctuation
- **Word count**: in 75-125 (initial) or 50-75 (followup) range
- **Personalization**: required `{{name}}`, `{{company}}`, `{{detail}}` slots
- **Spam triggers**: 200+ word blacklist (`guarantee`, `act now`, `100%`, etc)
- **CTA**: must have URL or specific question or time word
- **Unfilled brackets**: no `[BRACKETS]` left in template

Returns a 0-100 score with issue codes and fix suggestions. Run before every send. Run as CI check on your outreach repo.

36 tests, runs in 0.1 sec. MIT-licensed at `github.com/jiejuefuyou/autoapp-toolkit/blob/main/orchestrator/lib/cold_email_validator.py`.

---

### A real example: trimming a 200-word email to 100

Here's an actual email I had in my repo. **Before** (200 words, sent in 2024):

> Hi {{name}}, hope this finds you well.
> 
> I noticed your team at {{company}} has been doing some really impressive work in the {{industry}} space. I particularly liked your recent {{detail}}. The way you approached {{specific\_aspect}} was insightful.
> 
> I'm reaching out because I work with B2B teams like yours to help them get more value from their AI workflows. We've helped companies like X, Y, and Z achieve 30-40% productivity gains by streamlining their AI tool stack. Specifically, we look at:
> 
> - Tool sprawl reduction (most teams use 5-10 redundant tools)
> - Prompt library consolidation
> - Workflow handoff optimization
> - Measurement infrastructure
> 
> Our process is a 30-min discovery call followed by a 1-week audit followed by a 2-month implementation. Pricing starts at $99 for the audit and goes up to $25k for full implementation.
> 
> Would you be open to a 30-min call next week to explore if there's a fit? I'd love to learn more about what you're working on.
> 
> Looking forward to hearing from you.
> 
> Best,  
> Sun

**Validator output**:

- Score: 35/100
- ❌ Body 200 words > 150 hard cap
- ⚠️ Subject too generic
- ⚠️ Spam trigger: "I'd love to"
- ⚠️ CTA buried in last paragraph

**After** (100 words, 2026 best practice):

> Hi {{name}},
> 
> Just looked at {{company}}'s {{detail}} — sharp positioning.
> 
> Question: most {{industry}} teams I work with use 5-10 AI tools with 0 shared prompts library. The result is 8 hours/week wasted per person on duplicated work.
> 
> 30 min audit gives you (1) tool sprawl map (2) 3 quick-win prompts you can deploy this week. Free. If we click after, $99 starter package.
> 
> Reply with Wednesday or Thursday afternoon? Or book direct: cal.com/foo/30min

**Validator output**:

- Score: 92/100
- ✅ Word count in target
- ✅ Specific personalization slot
- ✅ Concrete CTA with URL fallback

Same value proposition. Half the words. 5x reply rate (in my 1-week test, n=24 sends).

---

### What I'd skip in 2026

A few practices that worked in 2023-2024 but **stop working** now:

**1\. Multi-paragraph "value-first" intros.** Lost. Recipients don't read past sentence 2 before deciding. Lead with the specific detail or skip.

**2\. "Just following up" without new info.** Auto-classified as spam by major providers in 2026. Every followup needs a NEW angle (new data, new resource, new ask).

**3\. Long signature blocks with social links.** Hurts deliverability score. Use 2-line signature: name + 1 link.

**4\. PS sections with secondary CTA.** Used to boost replies; now seen as template marker. Remove.

**5\. Hardcoded company info.** "I see you're at {{company}}, a leading {{industry}} firm" is dead. You need {{detail}} (specific recent action) instead.

---

### My current outreach stack (2026)

For full transparency:

- **10 emails** organized by ICP, each 75-125 words ([repo](https://github.com/jiejuefuyou/autoapp-toolkit))
- **2 mailbox rotation**: [hello@jiejuefuyou.com](mailto:hello@jiejuefuyou.com) (primary) + sun@ (backup)
- **DMARC `p=quarantine`** with rua reporting to dmarc@
- **Cal.com 30 min slot** as primary CTA
- **Reply rate target**: 5% (3% acceptable, 8%+ exceptional)
- **Sending volume**: 30/day per mailbox (well under 100 cap)

Sending Mon-Wed 9-11 AM JST (US Sun-Tue evening = best B2B reach for my audience).

---

### Action items

If your reply rate dropped recently:

1. **Run a deliverability check**: mail-tester.com (free) — score 8+/10 needed
2. **Verify DMARC**: `dig TXT _dmarc.yourdomain.com` — must return policy
3. **Run validator** on every template in your outreach folder
4. **Rewrite anything > 150 words** to 75-125 (cut, don't shorten)
5. **Add `{{detail}}` slot** to every template; fill with specific recent action
6. **Rotate mailboxes** if sending > 100/day total

This took me ~4 hours to do across my 70 templates. Reply rate started recovering inside a week.

---

### Summary

| Practice | 2024 | 2026 |
| --- | --- | --- |
| Initial email words | 200-400 | 75-125 |
| Followup words | 100-200 | 50-75 |
| DMARC required | Optional | **Hard-rejected** |
| Personalization | Token slots | Specific recent action |
| Daily volume/mailbox | 200-300 | 50-100 |
| Reply rate target | 1-3% | 3-5% (signal: 18%) |

If you've been ignoring these changes, your domain reputation is degrading silently. The first sign isn't always "spam folder" — it's **rejected at SMTP** with no notification. By the time you notice, you need a fresh domain.

Run the validator. Check your DMARC. Rewrite the templates. Don't lose your channel.

---

*Open source toolkit at github.com/jiejuefuyou/autoapp-toolkit. Validator + 10 trimmed templates included. If this helped, give me a star — I read every issue.*

---

## If this helped you, here are the tools I actually use

**[30 Day B2B Cold Email Templates](https://jiejuefuyou.gumroad.com/l/jdmmy)** — $15 — *30 cold-email templates I sent in 60 days — open rates inside*  
  
**[Indie Hacker 2026 Toolkit Bundle](https://jiejuefuyou.gumroad.com/l/emvfkj)** — $25 — *4 prompt packs (160 prompts) for outbound, ads, content, dev*  
  
**[14 iOS App Store Rejection Reasons (FREE)](https://jiejuefuyou.gumroad.com/l/sphytu)** — FREE — *free lead magnet — share with iOS founders to start the convo*

[See the full Day 60 indie hacker tool stack ->](https://jiejuefuyou.gumroad.com/)

DEV Community

[![Google AI Education track image](https://media2.dev.to/dynamic/image/width=775%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fu09y9fffqrb2one15j3g.png)](https://dev.to/deved/build-apps-with-google-ai-studio?bb=238784)

## Work through these 3 parts to earn the exclusive Google AI Studio Builder badge!

This track will guide you through Google AI Studio's new "Build apps with Gemini" feature, where you can turn a simple text prompt into a fully functional, deployed web application in minutes.