# Shubhra • Celestial Birthday Odyssey

An interactive Three.js birthday experience: an astronomical chronometer, a floating
celestial monolith, a haute pâtisserie cake with blow-out candles, five orbiting wish
crystals, and a fireworks finale. Everything runs in the browser — no build step,
no backend, no dependencies to install.

## Deploy to Vercel

**Option A — import the GitHub repo (recommended, auto-deploys on every push)**

1. Go to [vercel.com/new](https://vercel.com/new)
2. Import `AYTechOfficial/shubhra-birthday`
3. Vercel detects a static site and fills in the build settings automatically:
   - **Framework Preset:** Other
   - **Build Command:** *(leave empty)*
   - **Output Directory:** *(leave empty)*
4. Click **Deploy**

Every push to `main` now redeploys automatically.

**Option B — from the command line**

```bash
npm i -g vercel
vercel          # first run: link the project
vercel --prod   # ship it
```

## How the deploy is wired up

| File | Purpose |
| --- | --- |
| `index.html` | The entire experience. This name matters: Vercel serves `index.html` at the site root. |
| `vercel.json` | Declares the static (no-build) deploy, rewrites unknown paths back to `index.html`, and sets baseline security headers. |
| `.gitignore` | Keeps `.vercel/` and local artifacts out of the repo. |

There is no `package.json` on purpose. Vercel serves the repository root as static
output, which is the fastest possible path from push to live page.

## Personalising it

Everything the card shows lives in one file:

- **Name, date, and page title** — search `Shubhra` and `October 5` in [index.html](index.html).
- **The five wishes** — the `WISH_CARDS` array near the top of the script block. Each
  entry drives both a 3D orb in the scene and its modal.
- **Candle count** — `candlePositions` defines the five candles.
- **Melody** — `HAPPY_BIRTHDAY_NOTES` is the music-box note list (frequency in Hz).

## Local preview

```bash
npx serve .          # or: python3 -m http.server 5173
```

Open the printed URL, click **Begin Odyssey**, then advance with the buttons on the
bottom card. Click a candle to blow it out one at a time, or click anywhere in the
sky for a firework. Press `S` to launch one anywhere.

## Notes

- Audio starts on the first click (browser autoplay policy). The 🔊 button mutes it.
- The 3D card uses the Tailwind Play CDN, which prints a "not for production"
  console warning. That warning is expected and harmless for a single-file card —
  a compiled Tailwind build would be the route if this grew into a real app.
- `📷 Save Souvenir` downloads a PNG of the current scene.