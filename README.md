# KET Bulk SMS — PWA (installable web app) version

This folder turns your existing single-file HTML app into an installable
app on Android and iOS. No app store, no Android Studio needed.

## Files
- `index.html` — your original app, with a manifest link, iOS meta tags,
  and a service worker registration added (no other changes)
- `manifest.json` — tells the phone the app name, icon, colors
- `sw.js` — service worker, caches the app shell for instant/offline loading
- `icon-192.png`, `icon-512.png` — app icons (feel free to replace these
  with your own logo, same file names and sizes)

## Important: PWAs require HTTPS
"Add to Home Screen" / "Install app" only appears if the page is served
over **HTTPS** (or accessed as `localhost` during testing). Opening the
HTML file directly from your phone's file system won't trigger the
install prompt.

Since you're already using Cloudflare for your Worker proxy, the easiest
free hosting options are:

### Option A — Cloudflare Pages (recommended, same ecosystem you already use)
1. Go to the Cloudflare dashboard → Workers & Pages → Create → Pages
2. Upload this folder directly (drag-and-drop deploy, no Git needed)
3. You'll get a URL like `ket-sms.pages.dev` — share that link with staff

### Option B — GitHub Pages (also free)
1. Create a GitHub repo, upload these files
2. Repo Settings → Pages → deploy from the main branch
3. You'll get a URL like `yourname.github.io/ket-sms`

### Option C — Any existing web hosting you already have
Just upload these 5 files to any folder on your existing site (as long
as it's served over HTTPS).

## Installing it on a phone
1. Open the hosted URL in **Chrome** (Android) or **Safari** (iOS)
2. Android: tap the menu (⋮) → "Install app" or "Add to Home screen"
   (Chrome often shows this automatically as a banner too)
3. iOS: tap the Share icon → "Add to Home Screen"
4. An icon appears on the home screen — tapping it opens the app
   full-screen, no browser address bar

## Updating the app later
Just re-upload the changed `index.html` to the same hosting location —
staff don't need to reinstall anything, the service worker will fetch
the update automatically the next time they open the app (may take one
extra reopen to fully refresh due to caching).
