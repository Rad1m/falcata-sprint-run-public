# About Falcata Run

**Falcata Run** is a sprint training app **for Apple Watch**, with a companion iPhone app used only to review data after the session. It is designed specifically for track and field sprinters running the 100m, 200m, 400m, and 800m. It is the gold standard for sprint tracking — built from the ground up for the unique demands of short, explosive, all-out efforts that generic running apps were never designed to measure.

> **Important:** Falcata Run is **not a phone-in-your-waistband app**. The phone stays in your bag. All sensing happens on the Apple Watch, worn on the wrist, using its built-in 100 Hz accelerometer and gyroscope. There is no vest, no belt mount, no phone strapped to your lower back. The iPhone app is purely the analyst's workstation for reviewing charts, history, and deep sprint analysis once you're back from the track.

## The problem Falcata Run solves

Standard running apps — Strava, Nike Run Club, Apple Fitness, the stock Workout app — are built around steady-state endurance running. They sample GPS at 1 Hz, average data over minutes, and are tuned for 5Ks, 10Ks, half-marathons, and marathons. They simply cannot resolve the events that define sprinting:

- A **reaction time** of 180 milliseconds
- A **drive phase** that lasts 2 to 4 seconds
- A **finish line** crossed in 11 seconds, not 40 minutes
- **Form breakdown** that shows up in the last 20 meters of a 100m or the final curve of a 400m

Sprinting is a millisecond sport. You need a tool that was built with that in mind.

## What Falcata Run does differently

Falcata Run captures raw accelerometer, gyroscope, and gravity data at **100 Hz** — one sample every 10 milliseconds — directly on Apple Watch. Nothing is averaged, nothing is downsampled, nothing is lost. Every insight in the app is derived from that full-resolution signal.

On top of that raw data, Falcata Run runs purpose-built algorithms:

- A **3-phase piecewise linear fit** detects the true end of your sprint — the structural inflection point where acceleration transitions to deceleration — instead of waiting for you to slow down and walk off the track.
- **Velocity differentiation in the Earth frame** produces honest propulsive G-force readings (0.3–1.2 G, where they should be) instead of the 5–12 G artifacts that naïve accelerometer decomposition produces on a rotating wrist.
- **Curve compensation** on 200m and 400m sprints subtracts centripetal acceleration, corrects for body lean, and normalizes for the biomechanical asymmetry between your inside and outside arm on the bend.
- **Step detection via gyroscope peak/bottom analysis** counts every stride accurately — the arm swing is a cleaner signal than the noisy impact shocks your accelerometer sees.
- **Track-aware distance** uses Apple's sensor-fused distance samples, which match the actual arc of a 400m track, not the ~28% GPS polyline underestimate that every other app displays.

The result is a set of metrics that sprinters and coaches can actually trust.

## Built for the track, not the treadmill

Falcata Run is **watchOS-first by design**. When you step onto a track, your phone stays in your bag. The Watch becomes:

- A **starter pistol** with authentic, meet-simulation start sequences — "On your marks," "Set," the gun
- A **recording device** capturing 100 Hz motion through the entire sprint
- A **real-time display** of reaction time and sprint duration the moment you cross the finish
- A **coach** that tells you, after each rep, what to work on

Your iPhone is the analyst's workstation — charts, history, session insights, social sharing, deep sprint analysis, Game Center leaderboards. But the actual training happens on the wrist. No phone required. Everything syncs back when you're in range.

## The Mac app — Falcata Analyzer

For deeper desktop review there is a native macOS app, **Falcata Analyzer**. It opens the sprint sessions you export from your iPhone and reuses the exact same engine — so the charts on your Mac show the same math your Watch captured and your iPhone computed, never a separate desktop reimplementation.

On the bigger screen it adds a real review and editing workspace: synchronized velocity, drive, power, acceleration, arm-swing, and ground-contact charts on one shared playhead; individual charts popped out into side-by-side windows; and a video editor where you link your own sprint footage, align it to the acceleration onset, trim it, and burn a configurable telemetry overlay into an exported clip. You can also export charts as images or the underlying data as CSV. It's the same honest, single-source-of-truth philosophy, scaled up to a desk.

Falcata Analyzer also includes an optional **AI Sprint Coach** that turns your measured numbers into coaching — with a chat you can ask about any sprint across your whole imported history. You choose how it runs: fully on device with Apple Intelligence or a local open model, or with your own cloud API key (Anthropic, OpenAI, OpenRouter). The on-device options keep your data on your Mac; any cloud use is opt-in and shown clearly before anything is sent.

## The web app — Falcata Web Analyzer

Not every sprint comes from an Apple Watch. **Falcata Web Analyzer** ([app.falcatarun.com](https://app.falcatarun.com)) brings Falcata's marker-based video analysis to any sprint clip, in any modern browser, with nothing to install and no account to create.

You open a local video, scrub it frame by frame, and place markers: distance splits (Start / Distance / Finish) and ground contact time (contact → toe-off) spans. From those markers it derives segment velocities, launch acceleration, and a sprint summary, draws a live overlay exactly as it will export, and lets you save a PNG, a short sprint-window video clip (with audio), or a CSV. Units switch between metric and imperial, and your markers auto-save per video right in the browser.

It is deliberately the lightweight, hardware-free side of Falcata. The video never leaves your device — it is processed locally and never uploaded. Where Falcata Analyzer on the Mac overlays the telemetry your Watch captured, the web analyzer needs only the footage and your eye, which makes it ideal for quickly marking up a phone video of an athlete and sharing the result.

## The metrics

Every sprint is analyzed on these dimensions:

- **Reaction time** — measured to ±10ms accuracy from 100 Hz accelerometer signal
- **Drive force** (peak and average) — propulsive G through the acceleration phase
- **Cadence** — step frequency in Hz (e.g., 3.6 Hz = 215 steps per minute)
- **Stride length** — derived from verified step count and track distance
- **Arm drive efficiency** — ROM decay analysis detects form breakdown under fatigue
- **Time to max velocity** — how long it takes you to reach your top speed
- **Split times** — 10m and 50m intervals where possible
- **Drive phase efficiency** — horizontal impulse ratio (how much of your force goes forward, not up)
- **Effort %** — this sprint vs your PB at the same distance, so recovery reps get credit
- **Phase classification** — drive → transition → max velocity → maintenance, with distance-adaptive thresholds for 100/200/400

## Who Falcata Run is for

**Sprinters.** Whether you're a high school athlete running your first 100m, a collegiate 400m runner grinding through winter training, or a masters athlete still chasing PBs — Falcata Run gives you objective data where coaches used to rely on stopwatches and feel.

**Coaches.** Spot fatigue patterns across a training block. Compare reaction times rep by rep. See when a sprinter's arm drive starts to collapse. Identify the exact session where form broke down and load started to pile up.

**Teams and clubs.** Run block starts at practice with synchronized meet-simulation tone patterns. Game Center leaderboards bring competitive fire to Tuesday workouts.

**Self-coached athletes.** The Deep Sprint Analysis view shows you acceleration curves overlaid across weeks and months — your personal best in neon green, today's effort in white, the progression of stable peaks in a fading gradient of blue. You see your improvement visually.

## The philosophy

Sprinting is honest. The clock doesn't lie, the wind doesn't lie, and the body tells you when it's done. A sprint training app should be just as honest — no inflated metrics, no fake "performance scores," no features that paper over noisy sensor data. Every number in Falcata Run has a paper trail back to the raw 100 Hz signal. If the signal can't support a metric, Falcata Run doesn't show one.

That's the gold standard. Explode off the line. Own the first 30. Trust the data.

---

Learn more at [falcatarun.com](https://falcatarun.com).
