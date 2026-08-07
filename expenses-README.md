# LST-Expenses — Odoo 18

> A lightweight internal expense tracker: log income/outgoing transactions per user and per project, with automatic multi-currency balance calculation and a dashboard view.

**Status:** 🔒 Private repository — source available on request for review, freelance, or contract work.

## Overview

A focused, internal-use module for tracking day-to-day company expenses and income per user, without the overhead of Odoo's full Accounting suite. Useful for small teams that just need a simple, auditable ledger.

## Key Features

- **Per-user transaction ledger** — every Odoo user gets their own set of income/outgoing transactions, viewable directly from their user record.
- **Project-linked expenses** — transactions can optionally be tied to a project for cost tracking by initiative.
- **Automatic multi-currency conversion** — transaction amounts are converted to the company's currency automatically when computing totals, so mixed-currency entries still roll up correctly.
- **Live computed balances** — total income, total outcome, and net balance are computed fields, always up to date with no manual recalculation.
- **Quick-add wizard flow** — a one-click "Add Transaction" action opens a pre-filled form scoped to the current user.
- **Dashboard view** — a summary dashboard (via the `board` module) for a quick financial overview.

## Tech Stack

- Odoo 18 (Python ORM, computed fields, multi-currency conversion API)
- Depends on: `base`, `mail`, `board`

## Screenshots
<img width="1805" height="960" alt="Screenshot from 2026-08-03 21-50-18" src="https://github.com/user-attachments/assets/1bde4c88-b0d1-4a54-95be-ffbe7f46d08a" />
<img width="1805" height="960" alt="Screenshot from 2026-08-03 21-49-50" src="https://github.com/user-attachments/assets/da54f110-fb21-43a8-ba12-5cc62e7a9915" />
<img width="1805" height="960" alt="Screenshot from 2026-08-03 21-50-58" src="https://github.com/user-attachments/assets/c4644daa-d848-4569-8150-8c9000762f8c" />
<img width="1805" height="960" alt="Screenshot from 2026-08-03 21-51-10" src="https://github.com/user-attachments/assets/b7280ffa-206a-46ad-99c0-78264cc0893a" />
<img width="1805" height="960" alt="Screenshot from 2026-08-03 21-51-25" src="https://github.com/user-attachments/assets/7f08343e-c873-477f-a621-61df46ae2ee7" />


## Use Case Example

A small team logs daily outgoing expenses (office supplies, travel) and occasional incoming reimbursements directly against their user profile. Management opens the dashboard to see each team member's net balance at a glance, with all currency conversion handled automatically.

---
📩 Interested in this module or something similar for your Odoo instance? Reach out — contact details on my profile.
