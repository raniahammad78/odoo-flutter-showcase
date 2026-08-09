# DRS Extrusion Production Management — Odoo 18

> A shop-floor manufacturing module for tracking DRS roll extrusion machine production line-by-line: shift logs, per-extruder heating-zone temperatures, spray-weight quality sampling, and three role-based interactive dashboards — with bilingual (Arabic/English) Excel export matching the factory's paper log format.

**Status:** 🔒 Private repository — source available on request for review, freelance, or contract work.

## Overview

Built for a plastics/roll extrusion production line to replace paper shift logs with a structured Odoo module. Operators log every production roll — machine, shift, timing, personnel, product specs — while the system automatically tracks temperature deviations across each extruder's heating zones and computes quality/efficiency metrics in real time. Management gets a live OWL dashboard; personnel get role-specific views for supervisors and technicians.

## Key Features

- **Per-roll production logging** — machine number, shift, time in/out, supervisor, and a many2many list of technicians, tied to input/output roll numbers, product code, category, thickness, length, and final weight.
- **Auto-generated extruder/zone grid** — on creating a new record, the module automatically pre-fills a full reading grid for 8 extruders (A1–A4, B1–B4) × 5 heating zones each, ready for the operator to fill in speed, air pressure, set vs. actual temperature, and melt flow rate.
- **Automatic temperature deviation & warnings** — each extruder/zone line computes its own temperature deviation and flags a warning if it's out of range; the parent production record rolls this up into a single "has temperature warnings" indicator so problem rolls are instantly visible.
- **Quality sampling & variance tracking** — captures before/after weight samples at two sampling points (F11/F12), computes net weight automatically, and calculates spray-weight variance percentage between them as a quality/consistency signal.
- **Efficiency metrics** — weight-per-meter is computed automatically from final weight and roll length.
- **Bilingual Excel export matching the factory's existing paper log** — generates a formatted, right-to-left, print-ready Excel sheet (via `xlsxwriter`) per roll, with bilingual Arabic/English field labels, styled headers, and color-coded values — built to mirror the physical log sheet operators were already using, so adoption doesn't require relearning the paperwork.
- **Flexible export wizard** — export today's production, or a custom date range, optionally filtered to a specific machine.
- **Three role-based OWL dashboards:**
  - **Main dashboard** — live KPIs (total weight, rolls, length, average weight, active machines, quality score, scrap rate), trend/shift/quality charts (via Chart.js), filterable by date range, machine, shift, and supervisor, with auto-refresh.
  - **Supervisor dashboard** — manage and view employees flagged as production supervisors directly from a dedicated tab-based interface.
  - **Technician dashboard** — same pattern for extrusion technicians, with quick-add and overview tabs.
- **HR integration** — extends `hr.employee` with supervisor/technician flags so the existing employee database doubles as the personnel directory for shift assignments.

## Tech Stack

- Odoo 18 (Python ORM, computed fields, `xlsxwriter` for styled bilingual Excel export)
- OWL framework (Chart.js-backed dashboard, three separate dashboard components)
- Depends on: `base`, `hr`, `mrp`, `web`

## Screenshots


## Use Case Example

A plastics extrusion factory runs multiple DRS roll machines across shifts. Operators log each roll's production data directly in Odoo instead of paper; the system flags any heating-zone temperature that's drifted out of spec in real time, computes spray-weight consistency automatically, and lets a supervisor export the day's rolls to a bilingual Excel sheet formatted exactly like the log sheets the factory used before — for handoff, archiving, or compliance review.

---
📩 Interested in this module or something similar for your Odoo instance? Reach out — contact details on my profile.
