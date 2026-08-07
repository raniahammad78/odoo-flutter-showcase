# Company Visit Tracker — Odoo 18

> Manages recurring client visit contracts for service companies, auto-generates a per-client/per-month folder structure, and files visit reports automatically — with a Documents-app-style interface.

**Status:** 🔒 Private repository — source available on request for review, freelance, or contract work.

## Overview

Built for service companies that visit contracted clients on a recurring basis (maintenance, inspection, consulting, etc.). Instead of manually tracking who's due for a visit and where their reports live, this module automates the entire lifecycle: contract → scheduled visits → generated reports → organized folders → e-signature.

## Key Features

- **Visit contracts** — define start/end dates and visit frequency per client company.
- **Automatic folder structure** — a dedicated folder is created per contracted company, with automatic sub-folders for each month of the contract, mimicking Odoo's native Documents app UX.
- **Daily scheduled visit generation** — a cron job creates visit records automatically based on each contract's terms, with no manual scheduling needed.
- **Auto-generated placeholder reports** — each visit gets a PDF report placed directly into its correct company/month folder.
- **Kanban document browser** — a modern, Documents-app-like Kanban interface (custom JS/XML dashboard) for browsing folders and reports visually.
- **Extra visit wizard** — quickly log ad-hoc/unscheduled visits outside the normal contract cadence.
- **Not-contracted visit tracking** — separate model and reports for visits to clients without an active contract, so nothing falls through the cracks.
- **Client portal access** — built on `portal`, giving clients visibility into their own visit history where appropriate.
- **E-signature integration** — connects to Odoo's `sign` module for contract or report sign-off.
- **Custom sequences & access rules** — dedicated numbering and security rules for visits and folders.

## Tech Stack

- Odoo 18 (Python ORM, OWL front-end components, QWeb reporting, `ir.cron` automation)
- Depends on: `base`, `mail`, `portal`, `web`, `sign`, `account`

## Screenshots


## Use Case Example

A facilities maintenance company signs a 12-month contract with a client for monthly visits. The module automatically creates 12 monthly sub-folders under that client's folder, generates a visit record and placeholder report each month without manual input, and lets staff browse all of it in a clean, document-app-style Kanban view.

---
📩 Interested in this module or something similar for your Odoo instance? Reach out — contact details on my profile.
