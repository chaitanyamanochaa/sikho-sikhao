# Sikho-Sikhao 🏔️

Offline-first peer-learning system for a remote village classroom (ROOTS case study).

| File | What it is |
|---|---|
| `index.html` | Demo shell with a bottom switcher: **Teacher**, **Student phone**, **Side by side** |
| `teacher.html` | Teacher Dashboard: live pod telemetry, AI insights, AI Lesson Studio, Elder Stories Bank |
| `student.html` | Mobile "Hill Quest" app: Learn, Teach (time lock), Solo Check, Summit |

Everything is simulated in the browser. Finishing a round in the student app calls `generateSyncData()`,
logs the JSON to the console, and "Send to teacher" pushes it to the Teacher Dashboard, where Lesson 4092 updates.

## Run locally
Open `index.html`, or run `python3 -m http.server` and visit http://localhost:8000.
Demo tip: `student.html?lock=60` uses the real 60-second teach lock (default is 10 s).

## Deploy to GitHub Pages
1. Push these files to the `main` branch of a new repo.
2. Repo **Settings → Pages → Source: GitHub Actions**.
3. The included workflow publishes the site at `https://<user>.github.io/<repo>/`.

## Going truly offline
Tailwind, FontAwesome and Google Fonts load from CDNs. For the village (no internet), download them
once and reference local copies, so the laptop and phones need only the local router.

## Lesson codes, pods and the lab laptop (v2)
- **Lesson code** (e.g. 4092) = the topic. **Pod A, B, C, D** = the groups/phones taking it. Each phone has a fixed Phone number = Pod letter (Phone 1 = Pod A). In `student.html` tap the chip on the Summit screen (or use `?phone=2`) to change it.
- Phones push one JSON file each to the **router inbox**. In the lab, the laptop connects to the same router by LAN cable and uses **Download package from router** (button in the top bar and in the **LAN Collect** tab).
- **Live Pod Telemetry** groups pods under their lesson code. Tap a pod to analyse it, or tap **All participants report** for every student under that code.
- **Import phone JSON from USB / file** accepts the JSON that a phone logs or exports, as a fallback if the LAN is down.
