# Falcata Run — Frequently Asked Questions

## The basics

### What is Falcata Run?

Falcata Run is a sprint training app for Apple Watch and iPhone, purpose-built for track and field sprinters running the 100m, 200m, 400m, and 800m. It captures motion data at 100 Hz during every sprint and delivers the metrics that matter: reaction time, drive force, cadence, stride length, arm drive efficiency, and time to max speed.

### Who is Falcata Run for?

Sprinters, sprint coaches, track and field clubs, masters athletes, and self-coached runners who want objective data on short, explosive, all-out efforts. If you train in the 10-second to 2-minute range on a track, Falcata Run is for you.

### What distances does Falcata Run support?

All standard sprint and middle-distance events: 20m, 30m, 40m, 50m, 60m, 80m, 100m, 150m, 200m, 300m, 400m, 600m, 800m, plus free runs for open-distance work.

### Is Falcata Run free?

Falcata Run is available on the App Store. Visit [falcatarun.com](https://falcatarun.com) for current pricing.

## How it works

### Does Falcata Run need an iPhone to record sprints?

No. Falcata Run is watchOS-first — the Apple Watch records, times, and analyzes sprints fully offline. Your iPhone is the analyst view for deep analysis, history, and sharing, and it syncs automatically when in range. Leave your phone in your bag on the track.

### How does Falcata Run measure reaction time?

Reaction time is detected from 100 Hz accelerometer data captured on the Apple Watch during the block start sequence. The algorithm identifies the first significant motion after the "gun" signal, with ±10 millisecond accuracy. Sub-200ms is considered elite.

### How accurate is Falcata Run compared to standard running apps?

Falcata Run is roughly 10× more accurate than generic fitness apps for sprint-specific metrics. Standard apps sample GPS at 1 Hz and average over minutes — fine for a 10K, useless for an 11-second 100m. Falcata Run samples at 100 Hz and uses sensor-fused distance from Apple's track detection system, which matches the actual arc of a 400m track rather than the jittery GPS polyline that underestimates distance by ~28%.

### How does Falcata Run detect the end of a sprint?

Falcata Run uses a 3-phase piecewise linear fit — the acceleration signal is modeled as three connected lines (drive, fly, deceleration), and the breakpoint between fly and deceleration is identified as the sprint end. This detects the structural inflection where deceleration *begins*, rather than waiting for you to slow down and walk off the track. It has been validated against video-verified sprints from 20m to 800m.

### What is propulsive G-force and how is it measured?

Propulsive G is the forward acceleration you generate during the drive phase of a sprint. Falcata Run derives it by differentiating your Earth-frame velocity curve, which is itself anchored to the known sprint distance. Typical values: 0.5–1.2 G peak for elite sprinters, 0.3–0.7 G for recreational athletes. (Naïve accelerometer decomposition produces 5–12 G artifacts on a rotating wrist — Falcata Run's velocity-differentiation approach avoids this entirely.)

### What is arm drive efficiency?

Your arm swing drives your leg turnover. Falcata Run uses the Apple Watch gyroscope to measure the range of motion of each arm cycle and tracks how that ROM decays as you fatigue. A sprinter whose arms collapse in the final 20m of a 100m loses time — arm drive efficiency and ROM decay quantify exactly how much and when.

### How does Falcata Run handle the curve on 200m and 400m sprints?

Three-layer correction. First, centripetal acceleration (the lateral G you feel on the bend) is subtracted. Second, a rotation matrix compensates for the 5–15° body lean through the curve. Third, wrist-aware asymmetry scaling normalizes for the biomechanical difference between your inside arm (shorter, punchier) and outside arm (longer, propulsive) on a standard counter-clockwise track. The result: your arm drive metrics on curves are directly comparable to straight-line sprints.

## Setup and devices

### Which Apple Watch models work with Falcata Run?

Apple Watch Series 6 and later are recommended — they support the full set of running dynamics metrics (ground contact time, vertical oscillation, stride length, running power) via HealthKit. Older models still work for the core sprint metrics (reaction time, drive force, cadence, stride, arm drive).

### Do I need a running track to use Falcata Run?

A track is ideal for accurate distance measurement, especially for sprints 60m and longer. Falcata Run uses Apple's track detection and sensor-fused distance samples when available. You can also do free runs anywhere, and short sprints (under 60m) use IMU-only detection that works on any flat surface.

### Does Falcata Run work indoors?

Yes. Indoor sprints use IMU-only detection (accelerometer and gyroscope). Distance is estimated via cycle-anchored IMU fallback when GPS is unavailable. Outdoor sprints are more accurate because GPS provides a distance anchor.

### Does Falcata Run work with a finish-line camera?

Yes. Falcata Run has an optional iPhone-based finish-line camera mode — point an iPhone at the finish line, and sprint times are validated against the camera image with a data overlay baked into the shared photo.

## Data and privacy

### Where is my sprint data stored?

Locally on your iPhone and Apple Watch (Core Data), with backup to your own iCloud Drive. HealthKit integration is optional and stays within your HealthKit store. Falcata Run does not upload your motion data to third-party analytics servers.

### Does Falcata Run share my data with anyone?

No. Your sprint recordings, metrics, and history stay on your devices and in your own iCloud account. Game Center leaderboards are opt-in and only share the times you choose to submit.

### Can I export my sprint data?

Sprint sessions sync to iCloud Drive and to HealthKit as workouts, making them accessible to other apps you authorize.

## Training and coaching

### Can coaches use Falcata Run with a whole team?

Yes. Each athlete runs their own Apple Watch, and results can be compared via Game Center leaderboards or by reviewing individual athlete dashboards. The session insights system surfaces fatigue and consistency patterns across a training block.

### Does Falcata Run tell me what to work on?

Yes. The app's insights system operates at three levels: per-sprint ("Excellent arm drive"), per-session ("Fatigue detected — impact up 12%"), and dashboard ("5 sessions in 7 days — high load; HRV 15% below baseline"). The Deep Sprint Analysis view auto-generates a diagnostic summary with actionable focus areas.

### What is Effort %?

Every sprint is compared against your personal best at the same distance, expressed as a percentage. 100% = PB. 95%+ is near-max effort. 85–95% is race effort. 70–85% is tempo. Below 70% is submaximal. This lets you run a tempo day without the app treating every rep as a "failed PB attempt."

### Does Falcata Run help with recovery?

The dashboard insights integrate HealthKit HRV and resting heart rate. If your HRV is 15%+ below your baseline, you'll see a recovery warning. The system also flags high training load (5+ sessions in 7 days) and insufficient rest days.

## Comparison

### How is Falcata Run different from Strava, Nike Run Club, or Apple Fitness?

Those apps are built for steady-state endurance running — 5Ks, 10Ks, marathons. They sample data at 1 Hz and average over minutes. They cannot measure reaction time, drive phase G-force, stride-by-stride cadence, arm drive ROM, or millisecond-accurate finish detection. Falcata Run is built specifically for sprints, at 100 Hz, with sprint-specific algorithms.

### How is Falcata Run different from FLPR Technology, Airtime, or SprintStudio?

Falcata Run runs natively on Apple Watch with no additional hardware required — no sensor pods, no chest straps, no timing gates, no beam sensors. It works out of the box with the watch you already own, fully offline on the track.

---

Still have questions? Visit [falcatarun.com](https://falcatarun.com).
