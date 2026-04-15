# Safe Ministry Connections (SMX)

**Automating Safe Ministry compliance for Sydney Anglican churches — live safety checks, automated reporting, and zero admin burden for ministry teams.**

![License](https://img.shields.io/badge/license-Proprietary-blue.svg)
![n8n](https://img.shields.io/badge/automation-n8n-FF6A00.svg)
![Docker](https://img.shields.io/badge/containerized-Docker-2496ED.svg)
![Ubuntu](https://img.shields.io/badge/OS-Ubuntu-E95420.svg)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)

## About
SMX is a custom n8n automation system that connects Elvanto, Adminosaur, and ClickSend to deliver real-time Safe Ministry compliance monitoring and reporting for churches. It runs 24/7 on a self-hosted Hostinger VPS.

## Value Add
- **Eliminates administrative burden** on volunteer ministry teams by fully automating Safe Ministry compliance checks, reporting, and notifications — freeing them to focus on pastoral care rather than paperwork.
- **Delivers real-time safety monitoring** with automated compliance scans every 5 minutes during services and instant SMS alerts to leaders when issues arise.
- **Automates professional governance reporting** — generates accurate weekly, monthly, and historical compliance reports with zero manual effort.
- **Enhances emergency preparedness** with instant SMS roll-call tools (“roll” and “evac”) and UPS-backed service continuity.

## Key Features
- Live 5-minute check-in monitoring with automated leader alerts
- Scheduled weekly/monthly compliance and issue reports
- Emergency SMS roll-call system
- Smart room resolution from Elvanto/Adminosaur groups
- Multi-channel notifications (SMS + email)

## Tech Stack
- **Automation**: n8n (main + sub-workflows)
- **Scraping**: Playwright (headless browser)
- **Hosting**: Hostinger VPS (Ubuntu 24.04)
- **Containerisation**: Docker + Docker Compose + Traefik
- **Integrations**: ClickSend SMS, Hostinger SMTP

## Project Status
This repository contains **documentation and screenshots only**. Full workflow exports and Docker setup are not public for security and IP reasons.

Interested in deploying SMX in your church? Contact me — I can provide the complete package and adaptation support.

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
     alt="Weekly Missing Grade Follow-up Report" 
     width="48%" />
<img src="docs/screenshots/process-data-workflow.png" 
     alt="Weekly Compliance Issue Report" 
     width="48%" />
</div>

## Documentation
Full user and maintainer guides are included (room mapping, adding/removing rooms, n8n structure, VPS/Docker maintenance, troubleshooting).

## Contact
**Paul** — [@sevasek](https://x.com/sevasek)

---
Built to help churches serve safely and efficiently.