---
title: "I built 121 free online file tools as a side project - here is what I learned"
source: "https://dev.to/sylar_837ff17f3f5697f8305/i-built-121-free-online-file-tools-as-a-side-project-here-is-what-i-learned-28d"
author:
  - "[[Sylar]]"
published: 2026-06-11
created: 2026-06-14
description: "After months of nights and weekends, I launched Filuni - a free online toolkit with 121 tools for... Tagged with showdev, webdev, sideprojects, productivity."
tags:
  - "clippings"
---
After months of nights and weekends, I launched [Filuni](https://www.filuni.com/) - a free online toolkit with 121 tools for PDF, image, video, audio, and document processing. No signup, no upload limits, no watermarks.

## Why I built it

Every time I needed to merge a PDF or compress an image, I would land on a tool that either:

- limited me to 2 free uses per day,
- required an account for a 10-second task,
- slapped a watermark on my file, or
- wanted $12/month for basic operations.

So I built my own, and made it free.

## What is inside

121 tools across 12 categories:

- **PDF**: merge, split, compress, convert to Word/Excel/image, watermark, rotate, page numbers
- **Office**: Word/Excel/PPT/HTML/Markdown/CSV to PDF
- **Image**: compress, resize, crop, format convert, QR codes, EXIF viewer, watermark, collage
- **Video**: compress, convert, extract audio, video to GIF
- **Audio**: convert, compress, trim
- **Encryption**: AES/RSA, hash generators, Base64, digital signatures
- **Developer**: JWT decoder, regex tester, cron visualizer, cURL to code, JSON formatter/diff
- **Text / Color / Converters / Calculators**: word counter, diff, palettes, WCAG contrast, units, timestamps, BMI, loans...

## What I learned

1. **Users hate signup walls for simple tasks.** Removing all auth requirements was the single best UX decision.
2. **Client-side processing wins trust.** Most image/text/JSON tools run 100% in the browser (Canvas API, Web Workers) - files never leave your device. People notice and mention it.
3. **SEO is king for tool sites.** Every tool has its own landing page with FAQ and HowTo schema. Organic search is by far the biggest traffic source.
4. **Multi-language support compounds.** Filuni now ships in 11 languages (English, Spanish, Portuguese, German, French, Russian, Vietnamese, Korean, Japanese, Chinese Simplified & Traditional). Each locale opened a new market for the same codebase.

## Tech stack

Nuxt 3 + TailwindCSS + PWA. FFmpeg handles video/audio on the server, LibreOffice (via jodconverter) does Office to PDF. Server-processed files are auto-deleted after processing.

## Revenue model

Anchor ads only. No paywalls, no popups, no freemium tricks.

---

Try it: [www.filuni.com](https://www.filuni.com/) - I would love feedback on the UX, and suggestions for what tools to add next![MongoDB](https://dev.to/mongodb)Promoted

[![Gen AI apps are built with MongoDB Atlas](https://media2.dev.to/dynamic/image/width=775%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fi.imgur.com%2FlGiI0TQ.png)](https://www.mongodb.com/cloud/atlas/lp/try3?utm_campaign=display_devto-webdev_pl_flighted_atlas_tryatlaslp_prosp_gic-null_ww-all_dev_dv-all_eng_leadgen&utm_source=devto&utm_medium=display&utm_content=airevolution-v1&bb=238190)

## Gen AI apps are built with MongoDB Atlas

MongoDB Atlas is the developer-friendly database for building, scaling, and running gen AI & LLM apps—no separate vector DB needed. Enjoy native vector search, 115+ regions, and flexible document modeling. Build AI faster, all in one place.