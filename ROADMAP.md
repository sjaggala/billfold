# Roadmap — Billfold

_Last updated: 2026-11-01 — current as of: v1 built, deploying to Pages._

## Now (in flight)
- Publish to GitHub Pages and confirm the live URL works.

## Next (v1.x / near-term)
- **Reminders that actually fire** — browser Notifications API (opt-in) using the
  existing `remind` + `reminderDays` fields.
- **Overdue handling** — a filter/section and sort toggle; the data + labels
  already distinguish overdue.
- **Edit / delete individual payments** in a bill's history (currently
  append-only via "Mark as paid").
- **Mark-paid date picker** — let the user record a payment on a date other than
  today.
- **Dark mode** — tokens are already centralized in `:root`; add a `prefers-color
  -scheme` / toggle.

## Later (v2 / deferred)
- **Opt-in cross-device sync** — e.g. a cloud store or file-based sync. Deferred
  to keep v1 serverless and private.
- **PWA** — installable, offline-capable (add manifest + service worker).
- **Monthly calendar / timeline view** of upcoming bills.
- **Per-category budgets and spend summaries.**
- **Recurring income**, not just bills.
- **CSV import** (CSV export already exists).

## Done (recent)
- v1 app: bills CRUD + recurrence, categories/subcategories, cards/accounts,
  home, detail with history + next cycle, mark-as-paid, settings, JSON/CSV
  export, JSON import, sample data. (2026-11-01)
- Design system finalized: #2D00F7 + Hanken Grotesk + reduced type scale +
  refined icon palette. (2026-11-01)
