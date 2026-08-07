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

<H2>Main Dashboard</H2>
<img width="1854" height="1048" alt="image" src="https://github.com/user-attachments/assets/80f1ce20-6f90-4153-9f51-d0b27b2a51ad" />

<H2>Customers Dashboard</H2>
<img width="1854" height="1048" alt="image" src="https://github.com/user-attachments/assets/6629bb44-2c78-4226-adfa-6fe81a7aaf6f" />

<H2>Customer Form</H2>
<img width="1854" height="1048" alt="image" src="https://github.com/user-attachments/assets/f5fe4e30-d347-493a-b0ea-22af95c6af9c" />

<H2>Categories</H2>
<img width="1854" height="1048" alt="image" src="https://github.com/user-attachments/assets/e70490ef-c79c-41af-8727-6b541fe1717a" />

<H2>Machines</H2>
<img width="1854" height="1048" alt="image" src="https://github.com/user-attachments/assets/64dbf2a5-2a86-4cc1-8493-0e3e6b1b899c" />

<H2>Customer portal Main Dashboard</H2>
<img width="1854" height="1048" alt="image" src="https://github.com/user-attachments/assets/c2ccf7b9-ed20-480f-a5fc-d844b7403ade" />



## Use Case Example

A crane and lifting-equipment inspection company uses this module to manage its entire client base: each client's machines are registered, inspections are scheduled and reminders sent automatically, inspectors fill out checklists on-site, certificates are generated instantly, and the client can log into the portal to view their equipment's current certification status.

---
📩 Interested in this module or something similar for your Odoo instance? Reach out — contact details on my profile.
