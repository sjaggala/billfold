# Context — Billfold

_Last updated: 2026-11-01 — current as of: v1 data model and structure._

## Stack
- Plain **HTML + CSS + vanilla JavaScript**, one file: `index.html`. No
  framework, no bundler, no dependencies, no build step.
- **Hanken Grotesk** loaded from Google Fonts (the only external request).
- Persistence: browser **`localStorage`** under the key `billfold.v1`.
- Hosting: **GitHub Pages** (static). `.nojekyll` present.

## Structure (all inside `index.html`)
- `:root` CSS custom properties hold the whole design system (colors, radius).
  Change the palette there, not inline.
- One IIFE wraps all logic. Key parts, in order:
  - **storage**: `load()`, `save()`, `uid()`, `seed()` (default categories),
    `sampleData()` (optional demo bills).
  - **COLORS / ICONS**: the category color map and an inline-SVG icon set;
    `svg(name,size,stroke)` renders one. Icons are stroke SVGs, never emoji.
  - **helpers**: money/date formatting, `advance(date,cycle)` (recurrence),
    `cycleLabel`, lookups by id.
  - **router**: hash-based. `render()` reads `location.hash`, dispatches to a
    `screen*()` function, and replaces `#app`'s innerHTML. `go(hash)` navigates.
  - **screens**: `screenHome`, `screenDetail`, `screenBillForm` (add + edit),
    `screenSettings`, `screenAccounts`, `screenAccountForm`, `screenCategories`,
    `screenCategoryForm`.
  - **actions**: one delegated `click` listener keyed on `data-act` handles every
    button (nav, save*, del*, pay, export/import, etc.).

## Data model (`localStorage` → `JSON`)
```
{
  settings:   { currency:'$', defaultCycle:'monthly', reminderDays:3 },
  categories: [ { id, name, color, icon, subs:[string] } ],
  accounts:   [ { id, name, type:'card'|'bank', brand, last4, primary:bool } ],
  bills:      [ {
     id, name, amount, categoryId, sub,
     cycle: { every:Number, unit:'day'|'week'|'month'|'year' },
     nextDue:'YYYY-MM-DD', accountId, autopay:bool, remind:bool, notes,
     payments: [ { date:'YYYY-MM-DD', amount, accountId } ]
  } ]
}
```
- **Recurrence** is modeled as `{every, unit}` (e.g. monthly = `{1,'month'}`,
  "every 2 weeks" = `{2,'week'}`). `advance()` adds that interval to a date.
- **Mark as paid** pushes a `payments` entry and sets `nextDue = advance(nextDue,
  cycle)`. History is derived from `payments`; the bar chart/avg come from it.
- IDs are short random strings from `uid()`.

## Conventions
- Theme values live in CSS variables / the `COLORS` map — don't hardcode new hues
  inline; add a palette key.
- Every mutation calls `save()` then re-renders (`render()` or `go()`).
- All user text passed through `esc()` before being put in HTML.
- Icon-only buttons carry `aria-label`; forms use real `<input>/<select>/<label>`.

## Constraints
- **Static only** — no server, no secrets, no network calls except the font.
- Data is **per-browser, per-device**; there is no sync. Backup/restore is via
  JSON export/import (Settings → Data).
- Must work when opened from a plain static host (hash routing, no server
  rewrites) and degrade without `localStorage` (all access is `try/catch`).
- Keep it a single file unless a real need forces a split.

## Glossary
- **Bill** — a recurring charge being tracked. **Cycle** — its recurrence
  interval. **Next due** — the upcoming date. **Account** — a card or bank
  account a bill is paid with. **Category / subcategory** — the two-level
  taxonomy bills are filed under.

## Secrets
None. The app stores no credentials; "card" records hold only a nickname, brand,
and last 4 digits — never full numbers.
