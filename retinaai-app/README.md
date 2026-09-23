# RetinaAI Rural Screen — PWA

A single self-contained HTML file (`index.html`) — no build step, no dependencies to install.

## Important: don't just double-click the file

Service workers (what makes this installable + offline-capable) only work over `http://` or `https://`,
never over `file://`. If you double-click `index.html`, the page will still *look* right, but the
Install button and offline caching won't work. You need to serve it from a local web server.

## Option A — VS Code (recommended, easiest)

1. Install **VS Code**: https://code.visualstudio.com
2. Open this folder in VS Code (`File → Open Folder…`)
3. Install the **Live Server** extension (by Ritwick Dey) from the Extensions panel (`Ctrl+Shift+X`, search "Live Server")
4. Right-click `index.html` in the file explorer → **"Open with Live Server"**
5. It opens at something like `http://127.0.0.1:5500/index.html` — install prompt and offline mode will work there.

## Option B — Terminal, no IDE needed

Pick whichever you have installed:

```bash
# Python 3 (comes preinstalled on most Mac/Linux, and on Windows via python.org)
cd retinaai-app
python3 -m http.server 8000
# then open http://localhost:8000 in your browser

# Node.js (if you have it)
cd retinaai-app
npx serve .
# then open the URL it prints (usually http://localhost:3000)
```

## Testing the "Install App" feature

- **Android (Chrome)**: open the local server URL on your phone (same Wi-Fi, use your computer's
  local IP instead of `localhost`, e.g. `http://192.168.1.5:8000`), then tap "Install App" in the nav.
- **Desktop Chrome/Edge**: an install icon appears in the address bar, or use the in-page "Install App" button.
- **iOS Safari**: no auto-prompt (Apple restriction) — use Share → "Add to Home Screen" manually.

## Deploying it for real (so it's not just "local")

For an actual public link people can install from their own phones without your computer running,
host `index.html` for free on any static host, e.g.:

- **Netlify Drop**: https://app.netlify.com/drop — drag the `index.html` file in, get a live URL instantly
- **GitHub Pages**: push this folder to a GitHub repo, enable Pages in repo Settings
- **Vercel**: `npx vercel` from this folder

Any of these give you a real `https://` URL, which is required for install + offline to work outside
of local testing.
