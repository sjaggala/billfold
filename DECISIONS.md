# Decisions — Billfold

_Last updated: 2026-11-01_

Newest first. Never delete an entry; mark it superseded instead.

---

### 2026-11-01 — Vanilla single-file app, no framework or build
- **Decision:** Build the whole app as one `index.html` with inline CSS and
  vanilla JS.
- **Why:** Target is GitHub Pages for personal use. Zero toolchain means it just
  works when pushed, is trivial to edit, and has nothing to maintain or update.
- **Rejected:** React/Vite or similar — needs a build step and dependencies for
  no benefit at this size. A multi-file split — unnecessary for one screenflow.
- **Status:** active

### 2026-11-01 — Persist in browser localStorage, no backend
- **Decision:** Store all data in `localStorage` (key `billfold.v1`); offer JSON
  export/import for backup and moving between devices.
- **Why:** Keeps it free, private, and serverless; fits "personal use" and static
  hosting. No auth, no database, no running costs.
- **Rejected:** A cloud backend / database — overkill, adds cost, accounts, and a
  server to keep alive. Trade-off accepted: no automatic cross-device sync (see
  ROADMAP for a possible opt-in sync later).
- **Status:** active

### 2026-11-01 — Hash-based routing
- **Decision:** Route screens with `location.hash` (`#/bill/:id`, `#/add`, …).
- **Why:** Works on static hosting and even `file://` with no server rewrites;
  back/forward and deep links behave.
- **Rejected:** History API routing — would 404 on refresh under Pages without
  custom config.
- **Status:** active

### 2026-11-01 — Recurrence modeled as {every, unit}
- **Decision:** Represent any cycle as an interval `{every:N, unit:day|week|month
  |year}`; presets (Weekly/Monthly/Yearly) are just `{1, unit}`, "Custom" lets N
  vary.
- **Why:** One tiny model covers weekly, monthly, yearly and arbitrary intervals;
  `advance()` is a few lines and drives both next-due and "mark as paid".
- **Rejected:** Separate code paths per frequency; cron-like strings — more
  complexity than a personal tracker needs.
- **Status:** active

### 2026-11-01 — Design system carried over from the Design-canvas mockups
- **Decision:** Primary **#2D00F7**, **Hanken Grotesk**, reduced type scale
  (weights ≤600), and the refined 8-color category icon palette.
- **Why:** These were chosen and approved during the mockup phase; the built app
  should match what was signed off.
- **Rejected:** Re-deciding the look at build time.
- **Status:** active

### 2026-11-01 — Seed default categories; start with no bills/accounts; offer sample data
- **Decision:** First run seeds a useful category taxonomy (Housing, Utilities,
  Subscriptions, Insurance, Health, Other) but no bills or accounts; Settings has
  a one-tap "Load sample data" for trying it out.
- **Why:** A real tracker shouldn't arrive full of fake bills, but empty category
  pickers are annoying. Sample data makes evaluation easy and is reversible.
- **Status:** active
