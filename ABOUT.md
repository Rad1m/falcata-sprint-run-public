# About Falcata Run

**Falcata Run** is a sprint training app for **iPhone and Apple Watch**. It is designed for sprinters in any sport that trains explosive speed — track and field, football (40-yard dash), rugby, soccer, field hockey, and more. It is the gold standard for sprint tracking — built from the ground up for the unique demands of short, explosive, all-out efforts that generic running apps were never designed to measure. With an Apple Watch, every rep is captured automatically at 100 Hz on the wrist; without one, the iPhone is a complete sprint training log — live workouts at practice or sessions logged afterward.

> **Important:** Falcata Run is **not a phone-in-your-waistband app**. The phone stays in your bag. All sensing happens on the Apple Watch, worn on the wrist, using its built-in 100 Hz accelerometer and gyroscope. There is no vest, no belt mount, no phone strapped to your lower back. The iPhone app is the analyst's workstation — charts, history, deep sprint analysis — and, when there's no Watch on the wrist, the training notebook where sessions are logged by hand.

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

- A **3-phase piecewise linear fit** detects the true end of your sprint — the structural inflection point where acceleration transitions to deceleration — instead of waiting for you to slow down and stop.
- **Velocity differentiation in the Earth frame** produces honest propulsive G-force readings (0.3–1.2 G, where they should be) instead of the 5–12 G artifacts that naïve accelerometer decomposition produces on a rotating wrist.
- **Curve compensation** on 200m and 400m sprints subtracts centripetal acceleration, corrects for body lean, and normalizes for the biomechanical asymmetry between your inside and outside arm on the bend.
- **Step detection via gyroscope peak/bottom analysis** counts every stride accurately — the arm swing is a cleaner signal than the noisy impact shocks your accelerometer sees.
- **Track-aware distance** uses Apple's sensor-fused distance samples, which match the actual arc of a 400m track, not the ~28% GPS polyline underestimate that every other app displays.

The result is a set of metrics that sprinters and coaches can actually trust.

## Built for sprint work, not the treadmill

Falcata Run is **watchOS-first by design**. Wherever you train, your phone stays in your bag. The Watch becomes:

- A **starter pistol** with authentic, race-simulation start sequences — "On your marks," "Set," the gun
- A **recording device** capturing 100 Hz motion through the entire sprint
- A **real-time display** of reaction time and sprint duration the moment you cross the finish
- A **coach** that tells you, after each rep, what to work on

Your iPhone is the analyst's workstation — charts, history, session insights, social sharing, deep sprint analysis, Game Center leaderboards. But the actual training happens on the wrist. No phone required. Everything syncs back when you're in range.

## No Watch? The iPhone logs it

The Apple Watch is the flagship capture device, but it is optional. The iPhone app is a full sprint training log on its own, two ways:

- **Start a live workout** — leave the iPhone at practice and log each sprint between reps (distance, time, timing method, notes), repeat the last sprint in one tap, and run a Training Timer for warm-ups, drills, and recovery blocks. Heart rate and session time flow in via HealthKit where available, and the workout survives a force-quit intact.
- **Log a completed session** — enter the whole workout after practice: sprint sets as sets × reps with times and recoveries, training activities from warm-up to cooldown, an effort rating, and how you felt. A guided flow asks one question at a time; experienced athletes can jump straight to the quick composer.

Manual and Watch-recorded reps live in the same sessions, the same dashboard, the same trends and fastest-times lists. Every rep is labeled by how it was timed — Falcata Watch capture, hand timer, electronic timing, or video — and that provenance stays visible. Manual entries never pretend to be sensor data: they count toward your training volume and time progress, but they stay out of sensor-based biomechanics, leaderboards, and validation pipelines.

## The Mac app — Falcata Analyzer

For deeper desktop review there is a native macOS app, **Falcata Analyzer**. It opens the sprint sessions you export from your iPhone and reuses the exact same engine — so the charts on your Mac show the same math your Watch captured and your iPhone computed, never a separate desktop reimplementation.

On the bigger screen it adds a real review and editing workspace: synchronized velocity, drive, power, acceleration, arm-swing, and ground-contact charts on one shared playhead; individual charts popped out into side-by-side windows; and a video editor where you link your own sprint footage, align it to the acceleration onset, trim it, and burn a configurable telemetry overlay into an exported clip. You can also export charts as images or the underlying data as CSV. It's the same honest, single-source-of-truth philosophy, scaled up to a desk.

The Analyzer is also a coaching desk for a whole team. A **Team workspace** organizes athletes into squads with per-athlete progression dashboards (athletes get their own "My Progress" view), and a **guided analysis wizard** walks non-editors from "open a video" to results one step at a time. **AI Vision pose analysis** works on any footage — no sensor data required: it traces a frame-by-frame skeleton over the runner and derives cadence, ground contact time, torso lean, knee drive, and touchdown reach straight from the video, on device. Each sprint can keep its own units, so a 40-yard dash reads in yards next to a 100 m in meters, and exports can be landscape or vertical 9:16 with the overlay and skeleton baked in.

Falcata Analyzer also includes an optional **AI Sprint Coach** that turns your measured numbers into coaching — with a chat you can ask about any sprint across your whole imported history. You choose how it runs: fully on device with Apple Intelligence or a local open model, or with your own cloud API key (Anthropic, OpenAI, OpenRouter). The on-device options keep your data on your Mac; any cloud use is opt-in and shown clearly before anything is sent.

## The web app — Falcata Web Analyzer

Not every sprint comes from an Apple Watch. **Falcata Web Analyzer** ([app.falcatarun.com](https://app.falcatarun.com)) brings Falcata's marker-based video analysis to any sprint clip, in any modern browser, with nothing to install and no account to create.

You open a local video, scrub it frame by frame, and place markers: distance splits (Start / Distance / Finish) and ground contact time (contact → toe-off) spans. From those markers it derives segment velocities, launch acceleration, and a sprint summary, draws a live overlay exactly as it will export, and lets you save a PNG, a short sprint-window video clip (with audio), or a CSV. Units switch between metric and imperial, and your markers auto-save per video right in the browser.

It also brings AI to the browser. **AI Vision** runs on-device pose analysis on a marked section: it traces a frame-by-frame skeleton over the sprinter, detects each foot strike and measures ground contact automatically, counts contacts left and right, and flags overstriding (a foot landing ahead of the body). All of it runs locally with no upload — this is computer-vision pose analysis, distinct from the LLM-based AI Sprint Coach on the Mac.

It is deliberately the lightweight, hardware-free side of Falcata. The video never leaves your device — it is processed locally and never uploaded. Where Falcata Analyzer on the Mac overlays the telemetry your Watch captured, the web analyzer needs only the footage and your eye, which makes it ideal for quickly marking up a phone video of an athlete and sharing the result.

## The metrics

Every sprint is analyzed on these dimensions:

- **Reaction time** — measured to ±10ms accuracy from 100 Hz accelerometer signal
- **Drive force** (peak and average) — propulsive G through the acceleration phase
- **Cadence** — step frequency in Hz (e.g., 3.6 Hz = 215 steps per minute)
- **Stride length** — derived from verified step count and known distance
- **Arm drive efficiency** — ROM decay analysis detects form breakdown under fatigue
- **Time to max velocity** — how long it takes you to reach your top speed
- **Split times** — 10m and 50m intervals where possible
- **Drive phase efficiency** — horizontal impulse ratio (how much of your force goes forward, not up)
- **Effort %** — this sprint vs your PB at the same distance, so recovery reps get credit
- **Phase classification** — drive → transition → max velocity → maintenance, with distance-adaptive thresholds for 100/200/400

## Who Falcata Run is for

**Sprinters, in any sport.** Whether you're a high school athlete running your first 100m, a football player logging 40-yard dash times for the combine, a rugby or soccer player training breakaway speed, or a masters athlete still chasing PBs — Falcata Run gives you objective data where coaches used to rely on stopwatches and feel.

**Coaches.** Spot fatigue patterns across a training block. Compare reaction times rep by rep. See when a sprinter's arm drive starts to collapse. Identify the exact session where form broke down and load started to pile up.

**Teams and clubs.** Run explosive starts at practice — blocks, 3-point stance, or standing — with synchronized race-simulation tone patterns. Game Center leaderboards bring competitive fire to Tuesday workouts.

**Self-coached athletes.** The Deep Sprint Analysis view shows you acceleration curves overlaid across weeks and months — your personal best in neon green, today's effort in white, the progression of stable peaks in a fading gradient of blue. You see your improvement visually.

## The philosophy

Sprinting is honest. The clock doesn't lie, the wind doesn't lie, and the body tells you when it's done. A sprint training app should be just as honest — no inflated metrics, no fake "performance scores," no features that paper over noisy sensor data. Every number in Falcata Run has a paper trail back to the raw 100 Hz signal. If the signal can't support a metric, Falcata Run doesn't show one.

That's the gold standard. Explode off the line. Own the first 30. Trust the data.

---

Learn more at [falcatarun.com](https://falcatarun.com).
