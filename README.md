# FLOOSY (فلوسي)
Static, backend-free personal finance app. Single file: `index.html` (HTML + CSS + vanilla JS). Brand: Emerald & Lemon (light + dark).

## Run / Deploy (GitHub Pages)
1. Replace `index.html` and `README.md` in your repo (keep `SECURITY-REPORT.md` too).
2. Commit and push to the branch Pages serves (Settings → Pages). No build step.
3. Hard-refresh once (Ctrl+Shift+R). Your data is untouched: storage key `floosy.v1` and its format did not change.

## Design tokens
All colours, radii, spacing and shadows are CSS variables at the top of the `<style>` block (`--color-*`). Dark mode overrides them under `[data-theme=dark]`.

## Data
Saved automatically in this browser's localStorage (`floosy.v1`), this device only. Clearing browser data erases it, so export backups regularly. localStorage is NOT encrypted. Amounts are integer piastres.

## Backup format (JSON, `v: 1`)
`{ app:"FLOOSY", v:1, exportedAt:ISO-date, opening, tx[], cats[], budget{total,cat{}}, goals[], prefs{} }`
Import validates every field, shows a summary, offers "export current data first", requires confirmation, keeps the previous state under `floosy.prev`, and applies nothing if validation fails.

## Analytics (Google Analytics 4)
Disabled until you set your real ID in the first `<script>`: `window.FLOOSY_GA_ID='G-XXXXXXXXXX'`.
Once set, a settings checkbox lets each visitor opt in; only the page name is sent, never financial data. Reports are read in the Google Analytics dashboard (a private in-site admin page needs a backend, see SECURITY-REPORT.md).

## Appearance modes
Three modes: **Classic** (`light`), **Girly 🎀** (`girly`), **Dark** (`dark`). Choose in Settings → Appearance, or cycle with the quick button at the top. The choice is stored in the existing `prefs.theme` field of `floosy.v1` (old values `light`/`dark` stay valid; nothing else changed). Each mode is only a block of CSS variables (`:root`, `[data-theme=dark]`, `[data-theme=girly]`), plus a few decorative touches for Girly. Text-safe variants (`--color-primary-text`, `--color-income-text`, `--color-expense-text`) keep text readable where the brand pink or green is too light.
