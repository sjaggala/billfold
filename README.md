# Billfold — Bills Tracker

A simple, private bills tracker for personal use. Add recurring bills (weekly,
monthly, yearly, or a custom interval), organize them by category and
subcategory, tie each to a card or account, and see what's due next along with
each bill's payment history. Runs entirely in the browser — no account, no
server — and is built to be hosted for free on GitHub Pages.

## What it does

- **Home** — everything due, sorted by next date, with a "due this month" total.
- **Bill detail** — amount, next billing cycle, payment history, and a one-tap
  **Mark as paid** that records the payment and rolls the due date forward.
- **Add / edit bills** — name, amount, category + subcategory, billing cycle,
  next due date, the card/account it's paid with, reminder and autopay flags.
- **Settings (gear)** — manage **Cards & accounts** and **Categories /
  subcategories**, set currency, default cycle and reminder window, and
  **export / import / clear** your data.
- **Your data stays on your device** (browser `localStorage`). Use
  *Settings → Export* to make a JSON backup or move it to another device.

## Run it locally

It's a single static file. Either:

- Double-click `index.html` to open it in your browser, **or**
- Serve the folder (recommended, so the `#/` routes behave exactly like on
  Pages):
  ```bash
  cd billfold
  python -m http.server 8080
  # then open http://localhost:8080
  ```

## Publish to GitHub Pages

1. Create a new repository on GitHub (e.g. **billfold**). Public is required for
   free Pages.
2. From this folder:
   ```bash
   cd "billfold"
   git init
   git add .
   git commit -m "Billfold v1"
   git branch -M main
   git remote add origin https://github.com/<your-username>/billfold.git
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a
   branch**, pick **main** / **/ (root)**, Save.
4. Wait ~1 minute. Your app is live at
   `https://<your-username>.github.io/billfold/`.

The `.nojekyll` file is included so GitHub serves the files as-is.

## Project docs

- `CLAUDE.md` — orientation / entry point for any future work with Claude.
- `CONTEXT.md` — stack, structure, data model, conventions, constraints.
- `DECISIONS.md` — why the project is built the way it is.
- `ROADMAP.md` — what's next.
