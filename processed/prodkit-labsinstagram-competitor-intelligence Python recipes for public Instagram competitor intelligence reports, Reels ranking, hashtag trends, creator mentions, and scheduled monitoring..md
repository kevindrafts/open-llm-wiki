---
title: "prodkit-labs/instagram-competitor-intelligence: Python recipes for public Instagram competitor intelligence reports, Reels ranking, hashtag trends, creator mentions, and scheduled monitoring."
source: https://github.com/prodkit-labs/instagram-competitor-intelligence
author:
published:
created: 2026-05-09
description: Python recipes for public Instagram competitor intelligence reports, Reels ranking, hashtag trends, creator mentions, and scheduled monitoring. - prodkit-labs/instagram-competitor-intelligence
tags:
  - clippings
---
## Instagram Competitor Intelligence

Generate weekly Instagram competitor reports with Python.

Track public brand accounts, rank top-performing Reels, extract hashtag trends, detect creator mentions, and export client-ready Markdown / HTML reports.

> Built for developers, agencies, DTC brands, and social media analysts who want to turn public Instagram data into repeatable competitor insights.

This is not an Instagram API wrapper and it is not an automation bot. It is a practical open-source starter for turning public Instagram data into competitor reports.

[![Sample Instagram competitor report](https://github.com/prodkit-labs/instagram-competitor-intelligence/raw/main/assets/sample-report-preview.png)](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/assets/sample-report-preview.png)

## Who This Is For

- developers building public-data reporting workflows
- agencies creating weekly competitor reports
- DTC brands monitoring public competitor accounts
- social media analysts comparing Reels, hashtags, and creators

## Who This Is Not For

- follower, like, comment, or DM automation
- private account monitoring
- Instagram login automation
- bulk messaging or spam workflows
- unofficial claims of Meta or Instagram partnership

## What You Can Build

- Weekly competitor reports for brands or agency clients
- Reels performance rankings
- Hashtag trend summaries
- Creator and influencer mention research
- CSV exports for spreadsheets and dashboards
- Scheduled reports with GitHub Actions or cron

## Quick Start

Run the sample report with mock data first. No API key is required.

Clone the repo:

```
git clone https://github.com/prodkit-labs/instagram-competitor-intelligence.git
cd instagram-competitor-intelligence
```

Install dependencies:

```
pip install -r requirements.txt
```

Run with mock data:

```
python3 examples/06_generate_weekly_report.py --mock
```

Generated reports:

```
reports/sample_weekly_report.md
reports/sample_weekly_report.html
```

Optional syntax check:

```
python3 -m compileall examples src
```

## Example Output

See:

- [reports/sample\_weekly\_report.md](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/reports/sample_weekly_report.md)
- [reports/sample\_weekly\_report.html](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/reports/sample_weekly_report.html)
- [reports/export/](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/reports/export)

The report includes:

- competitor activity summary
- top posts and Reels
- hashtag trends
- creator mentions
- practical recommendations
- raw CSV-friendly metrics

## Recipes

Start with recipe 06 if you want the fastest end-to-end demo.

| Goal | Recipe |
| --- | --- |
| Generate a full weekly competitor report | `examples/06_generate_weekly_report.py` |
| Rank top-performing Reels and posts | `examples/03_rank_top_reels.py` |
| Compare multiple competitor accounts | `examples/05_compare_competitors.py` |
| Extract hashtag trends | `examples/04_extract_hashtags.py` |
| Find creator and brand mentions | `examples/09_extract_creator_mentions.py` |
| Export metrics to CSV | `examples/07_export_csv.py` |
| Export a multi-file report pack | `examples/12_export_report_pack.py` |
| Schedule recurring reports | `examples/08_schedule_with_github_actions.md` |
| Estimate API request usage | `examples/10_estimate_api_cost.py` |
| Structure an agency client report | `examples/11_agency_report_template.md` |
| Fetch recent public posts and Reels | `examples/02_get_recent_media.py` |
| Get public profile fields | `examples/01_get_profile.py` |

## Data Sources and Provider Setup

This project runs with mock data by default, so you can try it without any API key.

For real public Instagram data, use a provider adapter. The first adapter included in this repo is HikerAPI, and you can also implement your own provider by following `src/providers/base.py`.

- Mock data: free, no API key
- HikerAPI: included public-data provider adapter
- Custom provider: bring your own API or data source

For production decision notes, see:

- [docs/production/provider-comparison.md](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/production/provider-comparison.md)
- [docs/production/cost-control.md](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/production/cost-control.md)
- [docs/production/deployment.md](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/production/deployment.md)
- [benchmarks/README.md](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/benchmarks/README.md)

## When to Use a Real Data Provider

Mock data is useful for learning the workflow.

Use a real public-data provider when you want to:

- monitor real competitor accounts
- refresh reports weekly or daily
- export live posts and Reels data
- build dashboards for clients or internal teams
- compare public brand accounts over time

## Use Real Provider Data

Copy the environment example:

```
cp .env.example .env
```

Set a provider adapter and the provider-specific API key:

```
INSTAGRAM_DATA_PROVIDER=hikerapi
HIKERAPI_KEY=your_api_key_here
```

For the included HikerAPI adapter and custom provider setup, see:

- [docs/data-sources.md](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/data-sources.md)
- [docs/production/provider-comparison.md](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/production/provider-comparison.md)

Then run:

```
python3 examples/06_generate_weekly_report.py
```

## Production Notes

- Use mock data first.
- Start with small account lists.
- Estimate API usage before scheduling jobs.
- Cache data where possible.
- Do not commit API keys.
- Compare providers in the production docs before scaling scheduled runs.

## Documentation

- [Architecture](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/architecture.md)
- [Data model](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/data-model.md)
- [Metrics](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/metrics.md)
- [Provider adapter specification](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/provider-adapter-spec.md)
- [Troubleshooting](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/troubleshooting.md)
- [Privacy and data use](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/privacy-and-data-use.md)
- [Security policy](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/SECURITY.md)
- [Changelog](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/CHANGELOG.md)

## Use Cases

This project can be adapted for different public-data reporting workflows:

- [Agency Client Report](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/use-cases/agency-client-report.md)
- [DTC Brand Monitoring](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/use-cases/dtc-brand-monitoring.md)
- [Reels Content Research](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/use-cases/reels-content-research.md)
- [Hashtag Trend Tracking](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/use-cases/hashtag-trend-tracking.md)
- [Creator Mention Research](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/use-cases/creator-mention-research.md)
- [Weekly Report Automation](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/use-cases/weekly-report-automation.md)

## Templates And Integrations

Use these docs to turn workflow outputs into client-ready or team-ready deliverables.

Templates:

- [Agency Weekly Report](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/templates/agency-weekly-report.md)
- [DTC Brand Report](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/templates/dtc-brand-report.md)
- [Reels Breakdown Template](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/templates/reels-breakdown-template.md)
- [Hashtag Trend Template](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/templates/hashtag-trend-template.md)
- [Creator Mention Research Template](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/templates/creator-mention-research-template.md)
- [Executive Summary Template](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/templates/executive-summary-template.md)
- [Service Delivery Checklist](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/templates/service-delivery-checklist.md)

Integrations:

- [CSV Export](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/integrations/csv-export.md)
- [Google Sheets](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/integrations/google-sheets.md)
- [Notion](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/integrations/notion.md)
- [Feishu / Lark](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/integrations/feishu-lark.md)
- [Email Reports](https://github.com/prodkit-labs/instagram-competitor-intelligence/blob/main/docs/integrations/email-reports.md)

## Ethical Use

This project is for public data analysis and reporting. Do not use it for:

- private account data
- Instagram credential collection
- auto-DM, spam, scraping abuse, fake engagement, or account automation
- claiming official affiliation with Instagram, Meta, or any data provider

## Roadmap

- Mock data workflow
- Weekly Markdown / HTML report
- Reels and post engagement ranking
- Hashtag trend extraction
- Creator mention extraction
- GitHub Actions scheduling example
- Trust and documentation pack
- Use case documentation
- Report templates
- Google Sheets integration guide
- Notion integration guide
- Feishu / Lark integration guide
- Report pack CSV exporter
- Streamlit dashboard demo
- Provider-backed run examples
- Mock benchmark script
- Multi-client workspace prototype
- TikTok / YouTube Shorts competitor workflow