# Lucidity

A dream journal and lucid dreaming practice app. Installable PWA, works offline, stores everything on-device.

## Files

```
index.html          App (self-contained: all HTML, CSS, JS inline)
manifest.json       PWA manifest
service-worker.js   Offline caching
icons/              App icons (192, 512, 180 apple-touch, 32 favicon)
```

## Deploy to GitHub Pages

1. Push these files to a repo (root, or a `/docs` folder).
2. Settings -> Pages -> deploy from branch, pick the branch and folder.
3. Open the published URL on your phone. In the browser menu choose
   "Add to Home Screen" (iOS Safari) or "Install app" (Android Chrome).

All paths are relative (`./`), so it works whether it's served from the
domain root or a project subpath like `username.github.io/lucidity/`.

## Storage

The app uses `localStorage` on the web, and Claude's artifact storage when
run inside Claude. No server or account needed; data lives in the browser.
Clearing site data or uninstalling the PWA will erase saved dreams, so use
the journal's intent before wiping the browser.

## Updating

After editing `index.html` or any asset, bump the cache version in
`service-worker.js`:

```
const CACHE = 'lucidity-v1';   // -> 'lucidity-v2', etc.
```

That tells installed clients to drop the old cache and pull the new files.

## Notes

- The in-app reality-check session only runs while the app is open.
- All-day reminders work via the calendar (.ics) export, which fires even
  when the app is closed. There is no background scheduling on the web.
