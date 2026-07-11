---
title: "The Share Button Is the Product: Engineering a Viral Loop in Vanilla JS"
source: "https://dev.to/1436941541/the-share-button-is-the-product-engineering-a-viral-loop-in-vanilla-js-48n0"
author:
  - "[[yunjie]]"
published: 2026-07-05
created: 2026-07-08
description: "Most of us treat the share button as the last checkbox before shipping: drop in a navigator.share... Tagged with frontend, webdev, canvas."
tags:
  - "clippings"
---
Most of us treat the share button as the last checkbox before shipping: drop in a `navigator.share` call, maybe a Twitter intent URL, done. I did that too, until I built a personality quiz — and realized the share path *is* the product. Nobody needs a quiz result for themselves. The entire reason these things spread (remember the Soldier-Poet-King wave?) is that the result exists to be shown to other people.

So when I built [a Prince / Bandit / Mage quiz](https://princebanditmagequiz.org/) riding this year's animated-MV meme, I flipped my usual priorities. The quiz engine took an afternoon. The share funnel took a week. This post is about that week: encoding results into URLs with no backend, drawing Instagram-ratio share cards on a canvas, and a handful of small decisions that only matter once you assume every visitor arrived from someone else's screenshot.

One constraint up front, because it shaped everything: the whole site is static. No server, no database, no build step, no framework. The quiz engine is one IIFE in a single vanilla JS file. Everything below happens in the browser.

## A result page that doesn't exist

The first problem with a serverless quiz: what URL do you share? There's no `/results/abc123` because there's no database to put `abc123` in.

The answer is old and unglamorous: the URL hash. When the quiz finishes, the full result gets encoded into the fragment and stamped onto the current URL without a navigation:

```
var params = "result=" + key + "&p=" + score.prince +
             "&b=" + score.bandit + "&m=" + score.mage;
history.replaceState(null, "", "#" + params);
```

That one line buys a lot. Reload the page and an IIFE at the bottom of the file parses the hash and re-renders the exact result — same archetype, same percentage bars — without replaying fifteen questions. Copy the URL to a friend and they see *your* result, not a landing page.

The restore path has to be paranoid, though, because hashes are user-editable. Anyone can type `#result=mage&p=99&b=0&m=0`. So the restore function validates that the three scores sum to exactly the question count; if they don't, it keeps the claimed archetype but swaps in a neutral fallback distribution. Tampered links still render something sane — and a hand-typed `#result=mage&p=0&b=0&m=0` doesn't divide by zero into a page of NaN bars.

## The share links don't point at the quiz

Here's the decision I'd defend hardest. The social share buttons — X, Reddit, Tumblr, WhatsApp, Facebook — do **not** share the quiz URL with the hash. They share one of three static landing pages, one per archetype:

```
function shareUrl(key) {
  return location.origin + "/result/" + key + "/";
}
```

Why? Three reasons that only became obvious after thinking of shares as inbound doors rather than outbound exits:

1. **Crawlers can't see hashes.** A shared `quiz/#result=bandit` link gives every social platform the identical generic preview. A real `/result/bandit/` page gets its own title, description, and OG image — the unfurl card in the feed *is* the advertisement.
2. **Search engines can index them.** Three static pages targeting "prince bandit mage quiz \[archetype\]" queries cost nothing and catch people searching after seeing a friend's result.
3. **The landing page can pitch the quiz.** Someone clicking a friend's result doesn't want *your* fifteen answers replayed — they want to know what the thing is and take it themselves. Different job, different page.

The hash-URL still exists for the "copy link" button, where the receiver is a friend who genuinely wants to see your exact mix. Two share paths, two audiences, deliberately not unified.

## The result has to feel unrepeatable

A share loop dies if two friends compare results and they're identical. With three buckets and fifteen questions, collisions are guaranteed — so the trick is layering enough variation that the *rendered* result almost never repeats.

Scoring itself is a naive tally, but the tie-break is opinionated. Rather than `Math.max` order or randomness, ties resolve toward the *rarer* archetype, implemented as nothing more than iteration order plus `>=`:

```
function winnerOf(score) {
  // tie-break order favors the rarer archetype: mage > bandit > prince
  var best = "prince";
  ["bandit", "mage"].forEach(function (k) {
    if (score[k] >= score[best]) best = k;
  });
  return best;
}
```

If you're torn between the crowd-pleaser and the weird one, you get the weird one. Rare results get shared more; the tie-break quietly feeds the loop.

The bigger lever is what I called the *undercurrent*: a second reading based on your runner-up archetype. Six winner+secondary combinations each get distinct copy ("there's a Bandit riding in your verse..."), and when the secondary scores 3 or fewer out of 15 — nearly all answers pointing one way — it's replaced by a rare "pure verse" variant instead. That's nine narrative outcomes multiplied by a unique percentage mix, from a scoring function that's ten lines long. The variety lives in the copy, not the algorithm, and copy is cheap.

## Drawing the screenshot for them

People don't share links on Instagram; they share images. So the result screen renders a 1080×1350 share card (Instagram's portrait ratio) on a client-side canvas: radial-gradient parchment background, the tarot-style card art clipped through an `arcTo` rounded-rect path, the archetype name drawn onto a blank banner baked into the artwork, and three mini bars showing your percentage mix.

Canvas text rendering taught me two things the hard way:

**Fonts load late.** Draw before your webfont arrives and the canvas silently uses the fallback — the PNG looks off and no error tells you why. The fix is gating the entire draw on `document.fonts.ready`. It's a promise; await it, then paint.

**Art and text have to agree on coordinates.** Each card's artwork has its empty banner at a slightly different height, so each archetype carries its own `bannerY` ratio (0.846, 0.868, 0.848) and the name is drawn at `cy + ch * bannerY`. Hardcoding one offset looked fine on one card and misaligned on the other two.

The finished card goes through `canvas.toBlob` and gets cached, so when someone taps share, `navigator.share` can attach it as an actual image `File` — checked via `navigator.canShare({ files: [...] })` first. No Web Share support? Fall back to downloading the PNG plus a copy-caption button. The user should never dead-end.

## The pixel-level stuff that isn't optional

Last one, small but load-bearing: when the result appears, the card art must *already be there*. A placeholder flashing into a tarot card reads as jank, and jank on the money screen taxes the exact moment you want screenshotted.

Two-part fix. First, the moment the quiz starts, all three card images get preloaded — fifteen questions is plenty of time to fetch three webp files. Second, the reveal itself is gated on the decoder, not the network:

```
if (emblem.decode) {
  emblem.decode().then(reveal, reveal);
}
```

`img.decode()` resolves only after the image is fully decoded and paintable, so the result section stays hidden until the correct art can render in the same frame it appears. (Both promise branches call `reveal` — a broken image should degrade, not brick the page.) The percentage bars then animate via a double `requestAnimationFrame`, because setting a width and transitioning it in the same frame gets batched into no transition at all.

## What I'd take away

None of this is hard engineering — it's a few hundred lines of vanilla JS with no dependencies. What changed for me was the frame: for anything designed to spread, the share path deserves the same rigor as the core feature. Encode state where crawlers and friends can both use it, ship the unfurl page separately from the app page, and draw the screenshot yourself instead of hoping users take a good one.

If you want to see the loop end to end, [take the quiz](https://princebanditmagequiz.org/quiz/) and watch what the share modal hands you. I got The Mage, apparently. The tie-break may have been involved.[Sentry](https://dev.to/sentry)Promoted

[![Sentry image](https://media2.dev.to/dynamic/image/width=775%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fi.imgur.com%2FwQXpbvv.png)](https://sentry.io/welcome/?utm_source=devto&utm_medium=paid-community&utm_campaign=brand-fy27q1-quitbuggin&utm_content=static-ad-qb-peace-trysentry&bb=262857)