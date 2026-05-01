# Falcata Run

**The gold standard for sprint tracking.** A watchOS-first sprint training app for 100m, 200m, 400m, and 800m runners — built for sprinters, coaches, and track clubs who care about milliseconds.

🌐 [falcatarun.com](https://falcatarun.com)

---

## What it is

Falcata Run turns your Apple Watch into a starter pistol, a finish-line camera, and a professional sprint coach — all on your wrist, all without needing your phone at the track.

It captures motion at 100 Hz during every sprint and surfaces the metrics that actually matter: **reaction time, drive force, cadence, stride length, arm drive efficiency, and time to max speed.** Then it tells you what to fix, what to keep, and how to get faster.

**10× more accurate than standard running apps.** Generic fitness trackers are built for 5Ks and marathons. Falcata Run is built for the 10-second window where races are won.

## Who it's for

- **Sprinters** training the 100, 200, 400, and 800
- **Coaches** who need objective data on reaction time, form breakdown, and fatigue patterns
- **Masters athletes** chasing PBs into their 40s, 50s, 60s and beyond
- **Teams** running block starts at practice and simulating meet conditions

## What it measures

- ⚡ **Reaction time** — millisecond-accurate block start detection
- 🚀 **Drive force** — propulsive G-force through the acceleration phase
- 👟 **Cadence & stride** — step frequency (Hz) and stride length from gyroscope-verified step detection
- 💪 **Arm drive & ROM decay** — how much your form fades under fatigue
- 🏁 **Sprint end detection** — piecewise linear fit finds the true finish, not just when you stopped
- 📸 **Camera finish** — optional iPhone finish-line photo with data overlay
- 🏃 **Effort %** — how hard you ran vs your PB at the same distance
- 🔄 **Curve compensation** — corrects for centripetal force and body lean on 200m+ bends
- 📊 **Deep Sprint Analysis** — acceleration curve overlays, drive phase zoom, RT-vs-acceleration correlation

## See it in action

### On the Watch — track-side

| | | | |
|---|---|---|---|
| ![Apple Watch screen showing Open Sprint and Signal Sprint mode buttons — Falcata Run offers free-run mode and meet-simulation block start mode](screenshots/watch-mode-select.png) | ![Apple Watch screen showing 100m distance selection with Turn crown to change instruction and large green READY button](screenshots/watch-distance-100m.png) | ![Apple Watch Select Lane screen with track icon and lane 1 highlighted for curve-aware distance calibration on 200m and 400m sprints](screenshots/watch-lane-select.png) | ![Apple Watch sprint result screen showing 10.071s finish time in green, 281ms reaction time with +64ms delta from PB, and 101 bpm heart rate](screenshots/watch-sprint-result.png) |
| **Open or Signal Sprint** — free run or meet-simulation block start | **Distance select** — 100m, 200m, 400m, 800m, and more via crown | **Lane select** — for curve-accurate 200m and 400m distance | **Instant result** — finish time, reaction time, delta from PB, heart rate |

### On the iPhone — analyst view

| | |
|---|---|
| ![Falcata Run Dashboard on iPhone showing Sprint Analysis card with 200ms reaction time best, 0.3G peak drive force, and 244ms average, plus Recovery and Training insights including HRV status and weekly PB](screenshots/dashboard.png) | ![Sprint Analysis coach feedback for a 100m personal best at 13.600s, with green insight cards for explosive start, top speed matched, and strong finish across drive, float, and maintenance phases](screenshots/coach-feedback.png) |
| **Dashboard** — Sprint Analysis summary, recovery status, training load | **Coach feedback** — phase-by-phase insights and PB detection |
| ![Drive Phase chart showing acceleration curve across the first 1.5 seconds with foot strike markers at ~10G peaks, 282ms reaction time, and a Reaction Time bar chart showing 200ms best and 275ms average](screenshots/drive-phase-analysis.png) | ![World Rankings leaderboards screen for 100m, 200m, 400m, and 800m — Falcata Run submits valid sprint times to global leaderboards](screenshots/leaderboards.png) |
| **Deep Sprint Analysis** — drive phase zoom, foot strike detection, reaction time trend | **World leaderboards** — 100m, 200m, 400m, and 800m global rankings |
| ![Rep detail view showing Acceleration chart with Drive Force 0.18G and Drive Efficiency 63%, overlaid with sprint end and ground contact markers, plus Arm Swing gyroscope chart showing 28.89 rad/s peak rotation](screenshots/rep-detail-charts.png) | ![Finish line camera photo of a sprinter crossing a red outdoor track, showing the Camera Timed badge Falcata Run uses to validate sprint end times against visual evidence](screenshots/camera-finish.png) |
| **Rep detail** — acceleration, drive force, efficiency, arm swing analysis | **Camera finish** — validated sprint times with automatic data overlay |

## Why Apple Watch-first

Sprinters are on the track. Phones are in bags. Falcata Run runs fully offline on the Watch — recording, real-time metrics, start sequences, even meet-simulation tone patterns. Your iPhone is the analyst view: charts, history, sharing, deep analysis.

## Platforms

- Apple Watch (Series 6 and later recommended for full running-dynamics support)
- iPhone (iOS analyst companion)
- iCloud Drive for session backup
- HealthKit integration (workouts, heart rate, HRV, running dynamics)

## Links

- 🌐 Website: [falcatarun.com](https://falcatarun.com)
- 📖 [About Falcata Run](./ABOUT.md)
- ✨ [Full feature list](./FEATURES.md)
- ❓ [FAQ](./FAQ.md)

---

*Falcata Run is built by [Radim Simanek](https://github.com/Rad1m) and is a trademark of its respective owner. This repository contains marketing and documentation content only — the app's source code is private. See [LICENSE](./LICENSE) for usage terms on the documentation content.*
