# Billfold — Bills Tracker

_Last updated: 2026-11-01 — current as of: v1 shipped; single-file app complete and verified, ready to deploy to GitHub Pages._

## What this is
A private, personal bills tracker. One self-contained `index.html` (vanilla
HTML/CSS/JS, no build, no backend) that stores data in the browser and is hosted
on GitHub Pages. For Sravan's personal day-to-day use.

## Current state
Feature-complete v1: add/edit/delete bills with recurrence, categories &
subcategories, cards & accounts, home list with next-due dates, bill detail with
history + next cycle and "mark as paid", settings, and JSON/CSV export + import.
Data persists in `localStorage`. Smoke-tested headless with no JS errors.

## Current focus
Deploying to GitHub Pages. No open code work. Next candidate features are in
`ROADMAP.md`.

## Where everything lives
- `index.html` — the entire app (styles, markup scaffolding, and all logic).
- `CONTEXT.md` — stack, structure, the `localStorage` data model, conventions, constraints.
- `DECISIONS.md` — the decision log (why things are the way they are).
- `ROADMAP.md` — backlog and next steps.
- `README.md` — user-facing: run locally + deploy to Pages.
- `.nojekyll` — tells GitHub Pages to serve files as-is.

## Design system (locked)
- Primary **#2D00F7**; white/`#F6F7FB` surfaces; refined category icon palette
  (blue/amber/coral/violet/emerald/steel/pink/slate — see `COLORS` in `index.html`).
- Font **Hanken Grotesk** (Google Fonts); small type scale; weights ≤600.
- Mobile-first phone layout, centered in a max-width 460 column on desktop.

## Update protocol
- Decision made → append to `DECISIONS.md`
- Plan/scope change → `ROADMAP.md`
- Stable-fact change (data model, new convention) → `CONTEXT.md`
- Touched any file → bump its date + "current as of"
- These repo files are canonical for project state; don't duplicate them into
  Claude's core memory.
