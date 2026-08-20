# KCR Expenses App (PWA)

Kings Court Resort — common operating expenses register. Installable on Android
via Chrome, works offline after the first load, data stays on-device.

## Files

- `index.html` — the app (UI, logic, storage)
- `manifest.json` — PWA manifest (name, icons, colors, display mode)
- `service-worker.js` — offline caching
- `icons/` — app icons (192, 512, 512 maskable, apple touch icon, favicon)

## Deploy with GitHub Pages (free, HTTPS)

1. Create a new GitHub repo (e.g. `kcr-expenses-app`).
2. Upload all files in this folder to the repo root, **keeping the `icons/`
   folder structure intact**.
3. In the repo: **Settings → Pages → Source → Deploy from a branch**, pick
   `main` and `/ (root)`, then **Save**.
4. Wait 1-2 minutes. Your app will be live at:
   `https://<your-username>.github.io/<repo-name>/`

That URL is HTTPS by default, which is required for the service worker and
for Chrome's install prompt to appear.

## Install on Android (Chrome)

1. Open the HTTPS URL above in Chrome on your Android phone.
2. Tap **⋮ → Add to Home screen** (or you may see an **Install app** banner).
3. Confirm. The app icon appears on your home screen and opens full-screen,
   with no browser address bar.

## Verify it works offline

1. After installing (or even just visiting once in Chrome), turn on
   **Airplane mode**.
2. Open the app from your home screen.
3. It should load normally and you should be able to add/view expenses.
   Data you enter is saved with `localStorage`, so it's still there the next
   time you open the app — online or offline.

## Updating the app later

If you change `index.html`, `manifest.json`, or any icon, bump
`CACHE_VERSION` in `service-worker.js` (e.g. `kcr-expenses-v2`) before
redeploying — this tells installed copies to fetch the new files instead of
serving the old cached version.
