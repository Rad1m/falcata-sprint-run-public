# Falcata Run — Frequently Asked Questions

## The basics

### What is Falcata Run?

Falcata Run is a sprint training app for iPhone and Apple Watch, purpose-built for track and field sprinters running the 100m, 200m, 400m, and 800m. With an Apple Watch it captures motion data at 100 Hz during every sprint and delivers the metrics that matter: reaction time, drive force, cadence, stride length, arm drive efficiency, and time to max speed. Without one, the iPhone app is a complete sprint training log — live workouts at the track or sessions logged after practice.

### Do I need an Apple Watch to use Falcata Run?

No. The Apple Watch is the flagship capture device — it's what records the 100 Hz sensor metrics — but the iPhone app works fully without it. You can start a live workout on the iPhone and log each sprint between reps (with a Training Timer for drills and recovery), or log a completed session after practice: sets × reps, times, recoveries, warm-up through cooldown, effort, and how you felt. Manual and Watch-recorded reps share the same dashboard, trends, and fastest-times lists, and every rep is labeled by how it was timed (Falcata Watch, hand timer, electronic timing, or video). Sensor-based metrics like reaction time and drive force still require the Watch.

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

Generic fitness apps are built for steady-state running — they sample GPS at 1 Hz and average over minutes, which cannot resolve a 180ms reaction time, a 2-second drive phase, or an 11-second 100m finish. Falcata Run samples at 100 Hz and uses sensor-fused distance from Apple's track detection system, which matches the actual arc of a 400m track rather than the jittery GPS polyline that underestimates distance by ~28%.

### How does Falcata Run detect the end of a sprint?

Falcata Run uses a 3-phase piecewise linear fit — the acceleration signal is modeled as three connected lines (drive, fly, deceleration), and the breakpoint between fly and deceleration is identified as the sprint end. This detects the structural inflection where deceleration *begins*, rather than waiting for you to slow down and walk off the track. It has been tested against video-verified sprints from 20m to 800m.

### What is propulsive G-force and how is it measured?

Propulsive G is the forward acceleration you generate during the drive phase of a sprint. Falcata Run derives it by differentiating your Earth-frame velocity curve, which is itself anchored to the known sprint distance. Typical values: 0.5–1.2 G peak for elite sprinters, 0.3–0.7 G for recreational athletes. (Naïve accelerometer decomposition produces 5–12 G artifacts on a rotating wrist — Falcata Run's velocity-differentiation approach avoids this entirely.)

### What is arm drive efficiency?

Your arm swing drives your leg turnover. Falcata Run uses the Apple Watch gyroscope to measure the range of motion of each arm cycle and tracks how that ROM decays as you fatigue. A sprinter whose arms collapse in the final 20m of a 100m loses time — arm drive efficiency and ROM decay quantify exactly how much and when.

### How does Falcata Run handle the curve on 200m and 400m sprints?

Three-layer correction. First, centripetal acceleration (the lateral G you feel on the bend) is subtracted. Second, a rotation matrix compensates for the 5–15° body lean through the curve. Third, wrist-aware asymmetry scaling normalizes for the biomechanical difference between your inside arm (shorter, punchier) and outside arm (longer, propulsive) on a standard counter-clockwise track. The result: your arm drive metrics on curves are directly comparable to straight-line sprints.

## Setup and devices

### Which Apple Watch models work with Falcata Run?

Apple Watch Series 6 and later are recommended — they support the full set of running dynamics metrics (ground contact time, vertical oscillation, stride length, running power) via HealthKit. Older models still work for the core sprint metrics (reaction time, drive force, cadence, stride, arm drive). No Watch at all also works — see "Do I need an Apple Watch to use Falcata Run?" above; you can hide the Watch-specific tools entirely with the Apple Watch features preference in your profile.

### Do I need a running track to use Falcata Run?

A track is ideal for accurate distance measurement, especially for sprints 60m and longer. Falcata Run uses Apple's track detection and sensor-fused distance samples when available. You can also do free runs anywhere, and short sprints (under 60m) use IMU-only detection that works on any flat surface.

### Does Falcata Run work indoors?

Yes. Indoor sprints use IMU-only detection (accelerometer and gyroscope). Distance is estimated via cycle-anchored IMU fallback when GPS is unavailable. Outdoor sprints are more accurate because GPS provides a distance anchor.

### Does Falcata Run work with a finish-line camera?

Yes. Falcata Run has an optional iPhone-based finish-line camera mode — point an iPhone at the finish line, and sprint times are validated against the camera image with a data overlay baked into the shared photo.

### Can I record a full sprint video?

Yes. The Start Line Camera can record either a short slo-mo start or a full sprint. Full Sprint export creates a normal-speed video with Falcata telemetry overlaid: timer, reaction time, velocity/drive chart, foot-strike markers, and GCT bars. Long exports are capped at 20 seconds so processing stays practical on iPhone.

### Is there a Mac app?

Yes. **Falcata Analyzer** is a native macOS app (macOS 15 or later) for reviewing your sprints on a bigger screen. You export a sprint session from your iPhone and open it on the Mac, where you get synchronized velocity, drive, power, acceleration, arm-swing, and ground-contact charts on one shared playhead, pop-out chart windows you can arrange side by side, and a video editing workspace. It reuses the exact same engine as the Watch and iPhone, so the numbers never diverge.

It also works from footage alone: open any sprint video — no exported sprint required — mark Start / Finish / Distance points, and run on-device **AI Vision pose analysis** (skeleton overlay, video-derived cadence and ground contact time, torso lean, knee drive, touchdown reach). A **Team workspace** organizes athletes into squads with per-athlete progression dashboards, and a **guided analysis wizard** walks you from "open a video" to results step by step.

### Can I overlay my sprint data on my own video on the Mac?

Yes. In Falcata Analyzer you can link an external sprint video, align it to the acceleration onset, trim it, scrub it frame-accurately, and export a clip with a configurable telemetry overlay (H.264 MP4 or QuickTime, with resolution, frame-rate, and bitrate control). You can also export charts as PNG/JPEG images or the underlying lanes and markers as CSV. The linked video and your edits live in an app-side sidecar — your exported sprint file is never modified.

### Is there a web version?

Yes. **Falcata Web Analyzer** ([app.falcatarun.com](https://app.falcatarun.com)) runs entirely in your browser — no install, no account. You open a local sprint video, scrub it frame by frame, place distance markers (Start / Distance / Finish) and ground contact time spans, and read velocity, acceleration, and sprint stats from your markers. You can export a PNG, a short sprint-window video clip (with audio), or a CSV. Units switch between metric and imperial, and your markers auto-save per video in the browser. It also has **AI Vision** — on-device pose analysis on a marked section that traces a skeleton, measures ground contact automatically, counts foot strikes, and flags overstriding. Your video is processed locally and never uploaded.

### Do I need an Apple Watch to use the web analyzer?

No. The web analyzer works from the video alone — any sprint clip from any phone or camera. It does not use Watch telemetry; you mark the distances and ground contacts yourself, and it computes the rest. The Apple Watch, iPhone, and Mac apps are where the 100 Hz sensor analysis lives; the web app is the marker-based, hardware-free companion. For full-session telemetry review, use Falcata Analyzer on the Mac.

## Data and privacy

### Where is my sprint data stored?

Locally on your iPhone and Apple Watch (Core Data), with backup to your own iCloud Drive. HealthKit integration is optional and stays within your HealthKit store. Falcata Run does not upload your motion data to third-party analytics servers.

### Does Falcata Run share my data with anyone?

No. Your sprint recordings, metrics, and history stay on your devices and in your own iCloud account. Game Center leaderboards are opt-in and only share the times you choose to submit.

### Can I export my sprint data?

Sprint sessions sync to iCloud Drive and to HealthKit as workouts, making them accessible to other apps you authorize.

## Training and coaching

### Can coaches use Falcata Run with a whole team?

Yes. Each athlete runs their own Apple Watch, and results can be compared via Game Center leaderboards or by reviewing individual athlete dashboards. The session insights system surfaces fatigue and consistency patterns across a training block. On the Mac, **Falcata Analyzer**'s Team workspace takes this further: organize athletes into squads, assign their sessions and videos, and open a per-athlete progression dashboard — and because the Analyzer also analyzes plain video with AI Vision, athletes without a Watch still get a place on the roster.

### Does Falcata Run tell me what to work on?

Yes. The app's insights system operates at three levels: per-sprint ("Excellent arm drive"), per-session ("Fatigue detected — impact up 12%"), and dashboard ("5 sessions in 7 days — high load; HRV 15% below baseline"). The Deep Sprint Analysis view auto-generates a diagnostic summary with actionable focus areas.

### Does Falcata Run have AI coaching?

Yes, but only on the Mac. **Falcata Analyzer** (macOS) includes an optional AI Sprint Coach you can run fully on device (Apple Intelligence or a local open model) or with your own cloud API key (Anthropic, OpenAI, OpenRouter), plus a chat across your whole imported history. The Apple Watch and iPhone apps deliberately stay AI-free — they focus on reliable sprint biomechanics, camera-backed evidence, and transparent metrics. AI is never required to use Falcata Run, and on-device options keep your data on your Mac.

Separately, **AI Vision** — on-device computer-vision pose analysis — is available in two places: **Falcata Analyzer** on the Mac (skeleton overlay, video-derived cadence and ground contact time, torso lean, knee drive, touchdown reach, per-step metrics) and the **Web Analyzer** in the browser (skeleton overlay, automatic ground contact, foot-strike counts, overstride flags). Both run entirely on your device with no upload. That is pose analysis, not the LLM-based coaching the Mac app provides.

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
