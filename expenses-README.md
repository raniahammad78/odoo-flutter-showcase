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

*Available on request.*

## Use Case Example

A small team logs daily outgoing expenses (office supplies, travel) and occasional incoming reimbursements directly against their user profile. Management opens the dashboard to see each team member's net balance at a glance, with all currency conversion handled automatically.

---
📩 Interested in this module or something similar for your Odoo instance? Reach out — contact details on my profile.
