# Thickness Grouping Tool

> A Streamlit web app that takes a raw Excel sheet, cleans it, groups items by thickness value, and exports a styled, organized report — with live charts and metrics.

**Status:** 🔒 Private repository — source available on request for review, freelance, or contract work.

## Overview

Built to replace a manual Excel sorting/grouping workflow (common in manufacturing/inventory contexts — e.g. grouping pipes, sheets, or parts by material thickness). Users upload a raw `.xlsx` file, pick the relevant column, and get back a cleaned, grouped, and visually organized report they can download.

## Key Features

- **Excel upload & auto-cleaning** — strips hidden whitespace/non-breaking spaces and normalizes messy text data on upload.
- **One-click grouping** — select any column (e.g. thickness), and the tool cleans, sorts, and groups all rows by that value.
- **Live dashboard metrics** — total item count, number of unique groups, and data status shown instantly.
- **Interactive bar chart** — visual breakdown of item count per thickness group.
- **Styled, organized report view** — grouped rows are visually separated with subtotal rows (e.g. `TOTAL: 3.5 mm — 12 items`) and color-coded headers/totals directly in the app.
- **One-click Excel export** — downloads a multi-sheet `.xlsx` file: one sheet with the raw cleaned data, one with the fully styled, grouped report — ready to send to a client or colleague.
- **Fast reruns** — uses Streamlit's caching so re-interacting with the app doesn't reprocess the uploaded file each time.

## Tech Stack

- Python
- Streamlit (UI)
- pandas (data processing)
- openpyxl / xlsxwriter (Excel read/write + styled export)

## Screenshots

*Available on request — includes the dashboard view and a sample exported report.*

## Use Case Example

A materials or inventory team has a raw Excel export listing hundreds of items with a "thickness" column in inconsistent formats (extra spaces, mixed text/numbers). They upload it, select the thickness column, and instantly get a clean, grouped, subtotal-ed report they can hand off or archive — no manual Excel sorting required.

## Live demo

https://grouping-tool-c7z4mwwnfgm9p4h6rkpao3.streamlit.app/
---
📩 Interested in this tool or something similar built for your workflow? Reach out — contact details on my profile.
