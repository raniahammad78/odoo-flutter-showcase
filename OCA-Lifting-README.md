# Lifting — Odoo 18

> A full lifting-equipment inspection & certification suite: machine registry, inspection scheduling, checklists, certificates, and a customer-facing portal — built to OCA-style module standards.

**Status:** 🔒 Private repository — source available on request for review, freelance, or contract work.

## Overview

This is the most complete module in the set: it manages the entire lifecycle of lifting-equipment inspections (cranes, hoists, lifting gear, etc.) for a certification/inspection services company — from machine registration through inspection, certificate generation, customer notification, and portal access.

## Key Features

- **Machine & category registry** — track lifting machines by category, each with its own inspection history and documents.
- **Inspection workflow** — structured inspection records with checklists, tied to a numbering sequence (`ir_sequence`) for traceability.
- **Automated inspection reminders** — scheduled cron job checks upcoming/overdue inspections and triggers notifications via email templates.
- **Certificate & report generation** — dedicated QWeb reports for inspection certificates and "thorough examination" reports, ready for print or PDF hand-off to clients.
- **Customer portal integration** — extends `portal` and `website` so customers can view their machines' inspection status and certificates without backend access.
- **Website front-end views** — public-facing pages tied into the Odoo website module.
- **Role-based security** — dedicated security groups/rules (`inspection_security.xml`) separate what inspectors, managers, and portal customers can see.
- **HR integration** — links inspections to the `hr.employee` performing them.
- **Three custom dashboards** — a main dashboard, a machine-specific dashboard, and a customer dashboard, each built as OWL components (JS/XML/CSS) with custom brand-color styling.
- **Accounting integration** — connects to `account` for invoicing tied to inspection services.

## Tech Stack

- Odoo 18 (Python ORM, OWL front-end components, QWeb reporting, portal/website framework)
- Depends on: `base`, `web`, `contacts`, `website`, `mail`, `portal`, `account`, `hr`

## Screenshots

*Available on request — includes all three dashboards, portal views, and a sample certificate.*

## Use Case Example

A crane and lifting-equipment inspection company uses this module to manage its entire client base: each client's machines are registered, inspections are scheduled and reminders sent automatically, inspectors fill out checklists on-site, certificates are generated instantly, and the client can log into the portal to view their equipment's current certification status.

---
📩 Interested in this module or something similar for your Odoo instance? Reach out — contact details on my profile.
