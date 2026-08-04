# Remainder Module — Odoo 18

> Track product/license renewals and get automated email reminders before a purchase deadline passes.

**Status:** 🔒 Private repository — source available on request for review, freelance, or contract work.

## Overview

Built for businesses that sell products or licenses with a recurring purchase or renewal date (subscriptions, warranties, service contracts). Instead of tracking renewal dates in a spreadsheet, this module keeps them inside Odoo and automatically emails a reminder before the deadline.

## Key Features

- **Renewal tracking per partner/product** — each record links a customer (by partner number) to a product, quantity, and price, with a database-level constraint that blocks duplicate entries for the same partner + product.
- **Configurable reminder window** — choose to be notified 7, 15, 30, or 60 days before the purchase deadline.
- **Automated email reminders** — a scheduled action checks upcoming deadlines and sends reminders to a configurable recipient email per record.
- **Chatter & activity tracking** — built on `mail.thread` / `mail.activity.mixin`, so every record has a full audit trail and supports Odoo's native activity scheduling.
- **Custom reporting** — dedicated report view for reviewing upcoming/overdue renewals at a glance.
- **Clean display names** — records are labeled as `Product Name (Partner Number)` throughout the UI instead of a generic ID.

## Tech Stack

- Odoo 18 (Python ORM, `ir.cron` scheduled actions, QWeb reporting)
- Depends on: `base`, `mail`

## Screenshots

*Available on request.*

## Use Case Example

A company selling annual software licenses uses this module to make sure no license renewal is missed — sales reps get an automatic email 30 days before each client's license expires, giving them time to reach out before the client churns.

---
📩 Interested in this module or something similar for your Odoo instance? Reach out — contact details on my profile.
