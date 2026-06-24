# DAYPLAYER Line Producer

A single-file, offline-capable web app (installable PWA) for line producers running set. No backend, no build step — everything runs in the browser and saves to the device.

## Tabs

1. **Sign In / Out** — Add crew, log time in, meal 1, meal 2, wrap. Export the day's sheet as a PNG chart. Past days are archived and re-exportable.
2. **Schedule** — Upload sides/scenes as a PDF and page through them on set. Log scenes manually (number, description, pages), mark each as shot with a timestamp, and export the day's scene tracker as a PNG chart.
3. **Reports** — Upload 2nd AC reports and Script Supervisor notes for the editor. Files are stored on-device and downloadable any time.
4. **Purchases** — Log daily purchases with vendor, amount, note, and a receipt photo/PDF. Export everything as a `.zip`, organized into folders by date, each with a `summary.csv` and the original receipt files.

## Tech notes

- Pure HTML/CSS/JS, no framework, no build step.
- Data persistence: `localStorage` for structured records (crew rows, scenes, purchases), `IndexedDB` for file blobs (PDFs, receipts, reports) since they can be large.
- PDF rendering via [pdf.js](https://mozilla.github.io/pdf.js/) (loaded from cdnjs).
- Zip export via [JSZip](https://stuf.fr/jszip/) (loaded from cdnjs).
- Installable as a Home Screen app on iPhone/iPad via Safari → Share → Add to Home Screen. Works offline after first load thanks to the service worker.
- All data lives **only on the device it was entered on** — nothing is uploaded anywhere. Clearing Safari site data / browser storage will erase it, so export regularly.

## Hosting on GitHub Pages

1. Create a new repo (e.g. `dayplayer-line-producer`) and push these files to the `main` branch.
2. In the repo, go to **Settings → Pages**.
3. Under **Source**, choose **Deploy from a branch**, branch `main`, folder `/ (root)`.
4. Save. GitHub will publish at `https://<your-username>.github.io/<repo-name>/`.
5. Open that URL on your iPhone/iPad in Safari, then **Share → Add to Home Screen** to install it like a native app.

## File structure

```
.
├── index.html          ← the entire app (UI + logic)
├── manifest.json        ← PWA manifest (name, icons, colors)
├── service-worker.js    ← offline caching
├── icons/
│   ├── icon-192.png
│   └── icon-512.png
└── README.md
```

## Customizing icons

The included icons are placeholders in the DAYPLAYER amber/teal palette. Swap `icons/icon-192.png` and `icons/icon-512.png` with your own square artwork (same filenames) any time — no code changes needed.
