# Brain Check — iPhone Cognitive Tracker

A standalone, static, offline-capable progressive web app. Includes 20-trial reaction time, 8-trial backward-digit memory, 90-second timed arithmetic, longitudinal graph, local storage, CSV export, JSON backup and restore. No server, subscriptions, tracking, or external libraries.

## GitHub Pages setup (recommended)
1. Sign in to https://github.com and create a **new public repository** named `brain-check` (or another name). GitHub Pages on Free accounts generally requires a public repository. The app files are public, **your local test results are not uploaded to GitHub**.
2. On the repository page choose **Add file → Upload files**. Upload **the files inside this folder** into the root of the repo: `index.html`, `style.css`, `app.js`, `sw.js`, `manifest.webmanifest`, `icon.svg`, `icon-180.png`, `icon-192.png`, and `icon-512.png`. Click **Commit changes**.
3. Open **Settings → Pages**. Under **Build and deployment**, select **Deploy from a branch**, then select branch **main**, folder **/(root)**, and **Save**.
4. After the site publishes, its address should be `https://YOUR-USERNAME.github.io/brain-check/` (replace the user and repository names). Open the address in Safari on your iPhone.
5. In Safari tap **Share** → **Add to Home Screen** → turn on **Open as Web App** if shown → **Add**. Launch Brain Check from the new icon.
6. Take your first daily session. Under **Settings**, regularly export CSV files or JSON backups, ideally weekly. Safari data clearing or removing the web app can erase on-device history.

## Important operating details
- Keep your test conditions similar each day: same device, quiet room, similar time of day. Practice effects can occur over the first sessions.
- Reaction-time scores are *not* lab-grade due to screen/touch/browser timing. Do not compare across different devices.
- The three tasks have no normative clinical interpretation; this app is not a diagnostic or medical device.
- CSV includes raw individual test results as escaped JSON in the `raw` column. Importing CSV back into the app is **not** supported; use **JSON backup** for restoration.
- The app stores results in browser `localStorage` for the exact installed site/origin. Different iPhones/browsers may have different histories.
- Once opened online the first time, the service worker attempts to cache app assets for offline use. Test offline availability before relying on it.
- Updating the app may require refreshing the site and restarting the installed app. Browser storage restrictions may vary.

## Local testing on a computer
Run `python3 -m http.server 8000` inside this folder and open `http://localhost:8000` in a browser. Don't use `file://` for reliable offline service worker support.

## Methodology
- Reaction task: 20 visual signal trials; random foreperiod 1.8–4.4 seconds. Median valid RT (ms), number of valid responses >500 ms (slow responses/lapses proxy), number of false starts; population PVT cutoffs are not transferable to this simplified test.
- Memory task: 8 backward-digit trials; length 3,3,4,4,5,5,6,6. Shows digits for 0.95 + 0.63×length seconds. Exact-sequence accuracy and longest correctly repeated length.
- Arithmetic task: 90 seconds of addition, subtraction and multiplication, 4 answer choices. Number correct, attempted and accuracy percentage.
- Trends: up to last 60 sessions displayed; all sessions retained/exported locally.
