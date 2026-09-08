<h1 align="center">Local Hero</h1>
<p align="center">
  Progressive Web App, local-first, create & track habits easily: streaks, adherence, weekly reviews, backups (JSON/HRZ), PIN protection, and offline support.
</p>

<p align="center">
  Open App: https://konijn.github.io/local-hero/
</p>

---

## ✨ Features
- **PWA** installable (mobile/desktop), **offline** with Service Worker.
- **Local-first**: data stays on your device (IndexedDB + requested persistence).
- **PIN** unlock (4–8 digits) and **auto-lock**.
- **Habits** with AM/PM, **daily target** (>1), **days of the week**, reorder (drag & drop / ↑↓), archive.
- **Today** view with counter per habit (x/target) and undo (5 s).
- **Pro Statistics**: streak, 30-day adherence, **heatmap calendar**.
- **Weekly Review**: what worked, adjustments, and a “win” (history by week).
- **Backups**: `backup.json` (plain) and **encrypted `.hrz`** (AES-GCM + PBKDF2).
- **Import with merge**: merges data by habit name.
- **Multi-tab**: synchronizes changes between tabs using BroadcastChannel.
- **i18n** ES/EN and gentle in-app reminders during AM/PM periods.

## 🚀 Deployment on GitHub Pages
1. Create the public repository (e.g. `habit-tracker`) and upload:
   - `index.html`
   - `sw.js`
   - `manifest.webmanifest`
   - `assets/` folder with icons and README images
2. Settings → **Pages** → Source: *Deploy from a branch* → Branch: `main` → Folder: `/`.
3. URL: `https://YOUR_USER.github.io/YOUR_REPO/` (replace YOUR_USER/YOUR_REPO).
4. Open the URL, wait 2–3 seconds and refresh (installs the Service Worker). Then **Install** on your mobile device.

## 📱 Install as a PWA
- **Android (Chrome)**: ⋮ menu → *Install app* (or *Add to Home Screen*).
- **iPhone (Safari)**: **Share** → *Add to Home Screen*.
- iOS is already supported with meta tags and safe areas.

## ⚙️ Icon / Manifest Integration
Make sure you have in `<head>`:
```html
<link rel="manifest" href="manifest.webmanifest">
<link rel="icon" type="image/png" sizes="192x192" href="assets/icon-192.png">
<link rel="icon" type="image/png" sizes="512x512" href="assets/icon-512.png">
<link rel="apple-touch-icon" href="assets/apple-touch-icon-180.png">
<meta name="theme-color" content="#60a5fa">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<meta name="format-detection" content="telephone=no">
```

## 🧩 Service Worker
`sw.js` uses a **cache-first** strategy for static assets and a **navigation fallback** to `index.html` when offline. If you do not see changes after an update:
- Close the installed app and reopen the **URL** in the browser → refresh.
- Or increment the cache name in `sw.js` (e.g. `hr-cache-v7`) and commit.

## 🔐 Privacy and PIN
- Your data resides **only** on your device (IndexedDB/localStorage).
- The **PIN** and auto-lock are managed locally. If you forget it, you can erase data from the lock screen and **import** a backup.
- To store data in the cloud, use the password-protected **encrypted `.hrz`** backup.

## 🗃️ Backups (do not upload to the public repository)
Create a `.gitignore` containing:
```gitignore
# Do not upload your personal tracker data
habit-backup.json
*.hrz
```
If you uploaded a backup by mistake:
1) delete it in a new commit; 2) change the PIN; 3) generate a new backup. Optionally purge repository history with BFG or `git filter-repo`.

## 🧪 Quick Verification
- Check off habits, review **Statistics** and the **heatmap calendar**.
- Install as a PWA, enable airplane mode, and verify it opens **offline**.
- Test **backup.json** and **.hrz** (encrypted) and the **merge import** feature.

## 🐛 Common Issues
- **“Install app” does not appear on Android**: use *Add to Home Screen* instead.
- **iPhone not full screen**: remove the previous shortcut and repeat *Add to Home Screen*.
- **Drag and drop does not work on iOS**: use the **↑/↓** buttons to reorder.
- **Changes are not visible**: refresh 1–2 times; the Service Worker will update the cache.

## Origins
- This has been forked from https://github.com/mcruizgo/habit-tracker who made this with ❤️

---

<p align="center">
  Made with ❤️ for personal, local, and private use.
</p>
