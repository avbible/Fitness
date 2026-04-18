# Fit Tracker — Personal health/fitness PWA

Single-file web app at `index.html`. All data stays on your phone in `localStorage`.

## What it does
- Dashboard with today's weight, calories, protein, planned activity
- Workouts — pre-loaded with your routine (treadmill/crunch/leg press/OHP), tap-to-log sets
- Weight — daily entry + trend sparkline
- Food — voice logging + personal food library (grows as you use it)
- Vitamins — daily checklist + 7-day adherence grid
- Health — fasting window timer, tanning log, sleep log, profile

## Your preloaded data
- Profile: 51yo, 5'4", 185.6 lb, HVAC tech
- Fasting window: 3PM–10PM (eating)
- Strength routine: Thursday + rotating Mon/Tue
- Cardio: Wednesday brisk walk
- Tanning: 2×/week, 7 min
- Sleep: wind down 11:30PM, sleep midnight, 5mg melatonin
- 5 placeholder vitamins (D3, multi, magnesium, fish oil, melatonin) — replace with your real list via **Vitamins → Paste ChatGPT plan**

## Testing on desktop
Open `index.html` in Chrome. Voice input needs HTTPS or `http://localhost`.

## Getting it on your phone
Three options, easiest first:

### Option 1 — Run a tiny server on the office PC
```
cd C:/Claude/Fitness
python -m http.server 8080
```
Then on your phone (same WiFi): http://192.168.1.3:8080
(replace with office PC's LAN IP if different)
Voice may not work without HTTPS on LAN — see Option 2 or 3.

### Option 2 — Host on GitHub Pages (free, HTTPS)
1. Create a private repo
2. Push these files
3. Enable GitHub Pages → serves at https://<user>.github.io/<repo>/
4. On phone: open URL in Chrome → menu → "Install app" or "Add to Home screen"
5. Voice works because HTTPS ✓

### Option 3 — Wrap as Android app (later)
When you're happy with the UI, we wrap it with **Capacitor** to produce a real `.apk`:
```
npm init @capacitor/app
npx cap add android
npx cap copy
```
Same HTML, but installable without a server, works 100% offline, and can access native APIs (camera, notifications, HealthConnect) later.

## Data export / backup
Health tab → **Export all data** → downloads `fittrack-YYYY-MM-DD.json`.
Back up occasionally to avoid losing history if you clear browser data.

## Adjusting the routine
Edit `db.schedule.routine` in your browser console, or ask me to add a "routine editor" screen.

## Next features to consider
- Real PWA install (manifest + icons + service worker for offline)
- Notifications (vitamin reminders, workout days, fasting window alerts)
- Macro targets auto-adjust based on workout day vs rest day
- Progress photos
- Connect to a smart scale (Bluetooth) or HealthConnect
- Barcode scanner for food labels
