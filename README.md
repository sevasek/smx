# Safe Ministry Connections (SMX)

**Automating Safe Ministry compliance for Sydney Anglican churches — live safety checks, automated reporting, and zero admin burden for ministry teams.**

![License](https://img.shields.io/badge/license-Proprietary-blue.svg)
![n8n](https://img.shields.io/badge/automation-n8n-FF6A00.svg)
![Docker](https://img.shields.io/badge/containerized-Docker-2496ED.svg)
![Ubuntu](https://img.shields.io/badge/OS-Ubuntu-E95420.svg)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)

## About
SMX is a custom n8n automation system that connects Elvanto, Adminosaur, and ClickSend to deliver real-time Safe Ministry compliance monitoring and reporting for churches. It runs 24/7 on a self-hosted VPS.

## Value Add
- **Eliminates administrative burden** on volunteer ministry teams by fully automating Safe Ministry compliance checks, reporting, and notifications — freeing them to focus on pastoral care rather than paperwork.
- **Delivers real-time safety monitoring** with automated compliance scans every 5 minutes during services and instant SMS alerts to leaders when issues arise.
- **Automates professional governance reporting** — generates accurate weekly, monthly, and historical compliance reports with zero manual effort.
- **Enhances emergency preparedness** with instant SMS roll-call tools ("roll" and "evac") and UPS-backed service continuity.

## How It Works

SMX runs five main n8n workflows in orchestration:

| Workflow | Purpose | Trigger |
|---|---|---|
| `CheckinMonitor` | Polls Adminosaur every 5 minutes during services; sends SMS alerts when compliance issues are detected | Schedule |
| `WeeklyReport` | Aggregates check-in data and emails a weekly compliance issues report | Schedule |
| `MonthlyReportA` | Monthly all-clear or issues overview, plus missing Safe Ministry grade follow-up list | Schedule |
| `MonthlyReportB` | Bi-monthly compliance overview for extended tracking windows | Schedule |
| `Switchboard` | Handles inbound SMS commands — `roll` sends a room roll-call, `evac` broadcasts a full evacuation roll | Webhook |

Each main workflow delegates to sub-workflows for data processing, report generation, and notification dispatch — keeping logic modular and independently testable.

## Key Features
- Live 5-minute check-in monitoring with automated SMS alerts to leaders
- Scheduled weekly and monthly compliance and issue reports
- Emergency SMS roll-call system via inbound `roll` / `evac` keywords
- Smart room resolution from Elvanto and Adminosaur group mappings
- Multi-channel notifications (SMS + email)

## Tech Stack
- **Automation**: n8n (main + sub-workflows)
- **Scraping**: Playwright (headless browser for Adminosaur check-in data)
- **Hosting**: VPS (Ubuntu 24.04)
- **Containerisation**: Docker + Docker Compose + Traefik
- **Integrations**: Elvanto ChMS, Adminosaur, ClickSend SMS, SMTP

## What's in This Repo

| Path | Contents |
|---|---|
| `main-workflows/` | Five exported n8n main workflow JSON files — importable directly into n8n |
| `docs/screenshots/` | Example compliance reports and workflow screenshots |

> Sub-workflows, Docker Compose config, environment variables, and Playwright scraper scripts are not included for security and IP reasons. Interested in deploying SMX at your church? Contact me — I can provide the complete package and adaptation support.

## Screenshots
<div align="center">

<img src="docs/screenshots/monthly-compliance-report.png" 
     alt="Monthly Compliance Report - All Clear" 
     width="48%" />
<img src="docs/screenshots/monthly-compliance-report-not.png" 
     alt="Monthly Compliance Report - Issues Detected" 
     width="48%" />

<img src="docs/screenshots/weekly-compliance-issues-report.png" 
     alt="Weekly Compliance Issue Report" 
     width="48%" />
<img src="docs/screenshots/weekly-missing-grade-report.png" 
     alt="Weekly Missing Grade Follow-up Report" 
     width="48%" />

<img src="docs/screenshots/weekly-report-workflow.png" 
     alt="Weekly Report Workflow (n8n)" 
     width="48%" />
<img src="docs/screenshots/process-data-workflow.png" 
     alt="Process Data Workflow (n8n)" 
     width="48%" />
</div>

## Documentation
Full user and maintainer guides are included with the complete package (room mapping, adding/removing rooms, n8n structure, VPS/Docker maintenance, troubleshooting).

## 🚀 Roadmap & Future Releases

| Priority | Feature | Why It Matters | Implementation Sketch | Effort |
|---|---|---|---|---|
| High | **Expiry forecasting & proactive alerts** | Dedicated competitors like Safe Ministry Check already ship automated WWCC/Blue Card expiry tracking with reminder sequences — this is table stakes for the category, not a differentiator to skip. Lapsed certifications are the compliance failure mode with the highest real-world cost. | New sub-workflow queries Elvanto/Adminosaur volunteer records on a daily schedule, diffs certification expiry dates against 30/60/90-day thresholds, and routes to the existing SMS/email notification nodes already used by `WeeklyReport`. | Medium |
| High | **Adminosaur-native check-in sync** | The current Playwright scraper is the most fragile link in the system — a DOM change on Adminosaur's end silently breaks `CheckinMonitor`. Reducing polling latency from 5 minutes to near-real-time also tightens the safety-alert loop. | Replace the scraper node with a direct Adminosaur API/webhook call if one exists (worth a support inquiry); fall back to a more resilient scrape strategy (structured selectors + health-check alert on scrape failure) if no API is available. | Medium–High |
| Medium | **Multi-church support** | Several dioceses run near-identical Safe Ministry processes; a single-tenant-per-instance design caps SMX's reach to one parish. Multi-tenancy is the difference between a personal tool and something offered to other churches. | Parameterise the workflows by church/org ID, move per-church config (room mappings, contact lists) into a lookup table or lightweight DB, and add a per-church dashboard view to the reporting workflows. | High |

**Deprioritised for now:** AI-generated natural-language compliance summaries — interesting, but low leverage until the above reliability and coverage gaps are closed.

## Contact
**Paul** — [@sevasek](https://x.com/sevasek)

---
Built to help churches serve safely and efficiently.
