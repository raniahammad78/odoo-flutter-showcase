# Multi-Tier Approval & Credit Control Engine — Odoo 18

> A real-time financial exposure engine for the sales quotation lifecycle: combines unpaid invoices with un-invoiced confirmed orders to compute true credit risk, blocks orders that breach policy, and routes them through a parallel manager-approval workflow with automatic chatter activities.

**Status:** 🔒 Private repository — source available on request for review, freelance, or contract work.

> **Note:** This is an extension module, not a standalone app. It inherits and overrides Odoo's core `sale.order` and `res.partner` models via `_inherit`, adding credit-control logic directly onto the standard Sales workflow rather than replacing it.

## Business Problem & Solution

Standard ERP credit checks are usually static — they look at overdue invoices and stop there, ignoring orders that are already confirmed but not yet invoiced, and they rarely enforce discipline on unauthorized line-item discounts. This module closes both gaps:

- **Real-time financial exposure tracking** — dynamically computes a partner's true risk by combining posted unpaid invoices (`account.move`) with confirmed, un-invoiced sales orders (`sale.order`), rather than relying on invoice history alone.
- **Automated policy enforcement** — intercepts the core `action_confirm` pipeline to automatically halt any order that breaches a customer's custom credit threshold or carries a line-item discount greater than 15%.
- **Audit-ready workflows** — blocked orders are routed into a parallel "Pending Manager" approval queue, with a scheduled `mail.activity` automatically spawned and assigned to the relevant management team.

## Technical Architecture & Highlights

- **ORM lifecycle interception** — overrides `action_confirm()` to block stock picking/delivery creation until explicit management clearance is granted, rather than bolting a check on afterward.
- **Declarative XML UI patching** — injects contextual approval buttons, status badges, and visibility guards directly into standard Odoo 18 views via XPath, so the standard Sales UI gains the workflow without a full view rewrite.
- **Chatter & activity mixin integration** — built on Odoo's native `mail.thread` / `mail.activity.mixin` framework to log every approval state change and auto-schedule review tasks, keeping the audit trail native to Odoo rather than a bolt-on log table.

## Module Structure

```
sale_credit_approval/
├── __init__.py
├── __manifest__.py
├── models/
│   ├── __init__.py
│   ├── res_partner.py     # Custom credit limit & real-time exposure computation
│   └── sale_order.py      # Approval state machine, discount checks, & activity triggers
└── views/
    └── sale_order_views.xml   # Form view inheritance, state badges, & manager buttons
```

## Tech Stack

- Odoo 18 (Python ORM, `mail.thread` / `mail.activity.mixin`, XPath view inheritance)
- Depends on: `sale_management`, `account`

## Installation & Setup

1. Place the `sale_credit_approval` directory into your Odoo custom addons path.
2. Confirm the dependencies declared in `__manifest__.py`:
   ```python
   'depends': ['sale_management', 'account'],
   ```
3. Start your Odoo server and install/upgrade the module:
   ```bash
   python3 odoo-bin -c odoo.conf -u sale_credit_approval
   ```

## Usage & Verification

1. **Configure a customer's limit** — go to **Contacts**, select a customer, open the **Invoicing/Accounting** tab, and set their custom credit limit.
2. **Trigger the intercept** — create a new quotation in the **Sales** app. A line-item discount strictly greater than 15%, or an order that pushes the customer over their credit exposure limit, triggers the control engine on confirmation.
3. **Manager review** — the order transitions to **Pending Manager**, standard confirmation options are hidden, and a review activity is automatically scheduled in the chatter.
4. **Final approval** — authorized managers use the custom **Approve Order** / **Reject Order** header buttons to resolve the workflow and resume standard delivery processing.

## Use Case Example

A distribution company extends credit terms to repeat customers but has been burned by sales reps stacking confirmed-but-unbilled orders on top of already-overdue invoices — a risk static credit checks never caught. With this module, the moment a new order would push a customer's *combined* exposure (unpaid invoices + unbilled confirmed orders) over their limit, or a rep applies too steep a discount without authorization, the order is automatically frozen and routed to a manager for sign-off — with a full audit trail in the chatter, no spreadsheet tracking required.

## Screenshots

*Available on request — includes the Pending Manager state badge, approval buttons, and a sample chatter audit trail.*

## License

This project is licensed under LGPL-3.

---
📩 Interested in this module or something similar for your Odoo instance? Reach out — contact details on my profile.
