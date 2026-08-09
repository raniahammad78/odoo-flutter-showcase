# Lifting Inspector — Mobile App

Offline-first Flutter/Dart companion app to the **Lifting (OCA-Lifting)** Odoo 18
module. Built for field inspectors to carry out lifting-equipment inspections
on-site — often with no signal — and have everything sync back to Odoo
automatically once they're back online.

**Status:** 🔒 Private repository — source available on request.

## What it does

- Inspector logs in with their existing Odoo username/password.
- App downloads their assigned inspections (`inspector_id = me`, state in
  draft/pending) and caches them locally in SQLite.
- Inspector works through the checklist (accept/reject/N-A + remarks) and
  attaches evidence photos per line, fully offline — every action is saved to
  the local database instantly.
- Inspector sets the overall result (Safe / Conditional / Unsafe), captures an
  on-site signature, and submits for approval.
- As soon as the device regains connectivity, a background sync service
  pushes all queued changes to Odoo in order: checklist results → photos →
  inspection-level fields → the "submit for approval" action — then pulls
  fresh state back down.

## Architecture

```
lib/
  core/            app config, theme, Odoo field/model name constants
  data/
    network/       OdooClient — stateless JSON-RPC (common.login / execute_kw)
    db/            SQLite schema (offline cache + dirty/pending flags)
    models/        Inspection, ChecklistLine, EvidencePhoto
    repositories/  Session (auth + secure storage), InspectionRepository
                    (single source of truth the UI reads/writes — always
                    local-first, sync is a separate explicit step)
    sync/          ConnectivityService, SyncService (auto-flush on reconnect)
  features/
    settings/      first-run server URL + database entry
    login/          username/password login screen
    inspections/    list screen, detail/checklist screen, widgets
      widgets/      checklist_tile, photo_picker_grid, signature_pad_dialog
```

**Why stateless JSON-RPC instead of a session cookie?** Odoo's classic
external API (`common.login` → `object.execute_kw`, the same one XML-RPC
uses) re-sends the uid + password with every call instead of relying on a
server-side session. That's a better fit for mobile: no cookie jar to manage,
no session-expiry edge cases to handle after the app was backgrounded for
hours. Credentials are cached in the OS keychain via `flutter_secure_storage`,
not shared_preferences.

**Why checklist lines are never created client-side:** in your [Lifting](./Lifting-README.md)
module, `inspection.inspection.line` records are generated server-side when
an inspection's `machine_id` is set. The app only ever *reads* existing line
ids and *writes* results to them — this avoids the classic offline-sync
headache of reconciling client-generated temporary IDs with server IDs. The
one thing the app *does* create offline is `inspection.inspection.image`
records (evidence photos), and those always reference an already-known,
real line id, so that's a straightforward queued `create` call once online.

## ⚠️ One thing to decide on the Odoo side

`inspection.inspection.customer_signature` is defined in your module as
**"Manager Signature"**, auto-filled from the approving manager's employee
record. This app currently reuses that same field for the **on-site
signature captured during inspection**, which is a different thing
semantically (client/witness sign-off at time of inspection vs. manager
approval afterward).

For a quick pilot this is fine — but before rolling this out to real
inspectors, I'd recommend adding a dedicated field to `inspection.inspection`,
e.g.:

```python
onsite_signature = fields.Binary(string="On-site Signature", attachment=True)
```

and updating `OdooSchema.inspectionFields` in `lib/core/config.dart` plus the
one line in `inspection_repository.dart` that writes `customer_signature` —
that's the only place the field name is referenced.

## Getting this running

The code here is the `lib/` (and `pubspec.yaml`) of a Flutter project — you
still need the platform scaffolding (`android/`, `ios/`) that Flutter
generates, since that's environment/toolchain-specific and shouldn't be
hand-written.

1. Install the [Flutter SDK](https://docs.flutter.dev/get-started/install) if
   you haven't already, then from an empty folder:
   ```bash
   flutter create lifting_inspector_app
   ```
2. Copy `lib/` and `pubspec.yaml` from this project over the generated ones
   (keep the generated `android/`, `ios/`, `test/` folders).
3. Add the permissions listed in `android/PERMISSIONS.md` to the generated
   manifests.
4. Fetch packages:
   ```bash
   flutter pub get
   ```
5. Run on a connected device or emulator:
   ```bash
   flutter run
   ```
6. On first launch, enter your Odoo server URL and database name, then log in
   with an inspector's Odoo account.

## Known limitations / next steps (MVP scope)

- Certificate PDF viewing (the "view/download the final certificate" part of
  the full flow) isn't wired up yet — once an inspection is approved, the
  simplest path is fetching its certificate `ir.attachment` via
  `execute_kw` and opening it with a package like `open_filex` or
  rendering it with `syncfusion_flutter_pdfviewer`. Happy to build this next.
- No push notifications for newly assigned inspections — the list only
  refreshes on pull-to-refresh or app open. Could add via Odoo's `bus` module
  or a simple polling timer.
- Conflict handling is last-write-wins per record; if a manager edits an
  inspection in the Odoo backend while the inspector has unsynced local
  changes to the same fields, the inspector's sync will overwrite the
  backend's. Fine for the current single-inspector-per-inspection model, but
  worth revisiting if that assumption changes.
- No automated tests yet.

## Tech Stack

Flutter · Dart · sqflite (offline cache) · Odoo JSON-RPC (external API) ·
provider (state management) · flutter_secure_storage · image_picker ·
connectivity_plus

---
📩 Interested in this app or something similar built for your Odoo instance?
Reach out — contact details on my profile.
