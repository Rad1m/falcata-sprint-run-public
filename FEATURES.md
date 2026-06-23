# Falcata Run Features

A complete list of what Falcata Run does for sprinters and coaches.

## Core recording

- **100 Hz motion capture** on Apple Watch — accelerometer, gyroscope, and gravity sampled every 10 milliseconds
- **Fully offline recording** — no iPhone required at the track
- **Automatic sprint end detection** using a 3-phase piecewise linear fit (finds the true finish, not when you stop running)
- **Block start mode** with authentic meet-simulation tone sequences — "On your marks," "Set," the gun
- **Free run mode** for open-distance efforts without a fixed target
- **Camera finish** — optional iPhone finish-line photo with automatically overlaid sprint data
- **Start Line Camera** — optional iPhone recording from the start line, with Slo-mo Start and Full Sprint capture modes
- **Full Sprint video export** — normal-speed telemetry overlay video with timer, reaction time, velocity/drive chart, foot-strike ticks, and GCT bars

## Sprint metrics

- **Reaction time** — millisecond-accurate (±10ms), detected from 100 Hz accelerometer signal
- **Sprint duration** — true finish time, not recording duration
- **Peak propulsive G-force** — maximum acceleration during the drive phase
- **Average drive G** — average propulsive force from start to peak velocity (deceleration excluded so recovery doesn't dilute effort)
- **Drive phase efficiency** — horizontal impulse ratio (% of force pushing you forward vs up)
- **Time to max velocity**

## Stride and cadence

- **Step count** via gyroscope Z-axis peak/bottom detection (video-verified accurate)
- **Stride frequency** in Hz (e.g., 3.6 Hz) and steps per minute
- **Average, peak, and minimum cadence** — all derived from the same source of truth, so avg never exceeds peak
- **Stride length** — computed from verified step count and known or estimated distance

## Form and technique analysis

- **Arm drive efficiency** — range-of-motion tracking cycle by cycle
- **ROM decay** — measures how much your form fades under fatigue, with distance-aware thresholds
- **Phase classification** — each sprint segmented into drive → transition → max velocity → maintenance, with logic adapted for 100m / 200m / 400m
- **Coaching focus** — phase-specific cues (explosive push, relaxed shoulders, hold arm drive, fight fatigue)
- **Step-by-step breakdown** — per-cycle efficiency and power index

## Distance and splits

- **Track-aware distance** using Apple's sensor-fused distance samples (matches actual arc, not jittery GPS polyline)
- **Split times** at 10m and 50m intervals where data supports it
- **Lane-adjusted distances** for curved sprints
- **Free-run distance estimation** — GPS-fused, GPS-route, or cycle-anchored IMU fallback

## Curve-aware correction (200m and 400m)

- **Centripetal acceleration removal** — subtracts the lateral G you experience on the bend
- **Body-lean compensation** — rotation matrix corrects gyroscope signal for the 5–15° lean through curves
- **Wrist-aware arm asymmetry scaling** — normalizes for the inside arm vs outside arm biomechanical difference on a standard counter-clockwise track
- **Bell-curve weighting** — smooth entry and exit from curve correction so the signal stays continuous

## Deep Sprint Analysis

- **Sprint curve overlay** — your acceleration curves layered across weeks and months, with PB in neon green, current sprint in white, and historical stable peaks in a gray→blue age gradient
- **"Progression narrative" sampling** — algorithmic selection of the median of the top 3 sprints per time bucket (filters out flukes and lazy warmups)
- **Drive phase zoom** — first 2 seconds with automatic foot strike detection
- **RT vs peak acceleration scatter** — Pearson correlation between your start and your top-end
- **Diagnostic summary card** — auto-generated, actionable insights comparing recent performance to your averages

## Insights system (three levels)

- **Sprint insights** — single-sprint feedback: "Excellent arm drive," "Personal best reaction time!"
- **Session insights** — aggregate patterns: "Consistent performance (8% variance)," "Fatigue detected — impact up 12%," "Strong finish"
- **Dashboard insights** — training load and recovery: "5 sessions in 7 days — high load," "HRV 15% below baseline"
- Severity-coded: green (positive), gray (neutral), yellow (attention), red (warning)

## Effort %

- Each sprint compares against your PB at the same distance
- Color-coded zones: near-max (95%+), race effort (85–95%), tempo (70–85%), sub-maximal (<70%)
- Automatic PB badge when you beat your previous best
- Excludes false starts, free runs, and GPS-mismatched long sprints from the PB pool

## Personal bests and history

- **Per-distance PB tracking** (20, 30, 40, 50, 60, 80, 100, 150, 200, 300, 400, 600, 800m)
- **Camera-verified PBs** take priority over non-camera
- **Session history** with full sprint breakdown
- **Trend analysis** across time ranges (week, month, year)

## Health and recovery

- **HealthKit integration** — workouts, heart rate, HRV, resting HR
- **Running dynamics** from Apple Watch Series 6+ — Ground Contact Time, vertical oscillation, stride length, running power
- **HRV-based recovery insight** — warns when you're training under stress
- **Training load tracking** — sessions per week, rest days, high-load alerts

## Sharing and social

- **Sprint share cards** — branded 1080×1350 images with your time, distance, reaction time, date, and logo
- **Camera finish overlay** — share the actual finish-line photo with data band
- **Start Line Camera video overlay** — export a full-sprint video with sprint telemetry; long exports are capped at 20 seconds for practical processing
- **Game Center leaderboards** — compete with teammates and athletes worldwide
- **Live Activities** — sprint session status on the iPhone lock screen

## Desktop analysis (macOS — Falcata Analyzer)

A native macOS app that ingests your exported sprint sessions and reuses the **same engine** as the Watch and iPhone — the Mac shows the exact math your wrist captured, with no separate desktop calculation path.

- **Open exported sprint sessions** — browse every sprint with its stored metrics and canonical charts (acceleration, velocity, drive force, power, arm swing, foot-strike, ground contact time)
- **Synchronized charts** — one shared, scrubbable playhead across all lanes; hover or click-drag to scrub; select a time range to read each lane's average over the interval
- **Per-lane focus** — maximize a single chart, or open individual charts in separate native macOS windows and arrange them side by side
- **Video editing workspace** — link an external sprint video, align it to the acceleration onset (GO), trim the useful range, and play/scrub with frame-accurate seeking
- **On-video marker editing** — create and edit Start / Finish / Distance markers on the video timeline or directly on the charts; edits persist in a per-sprint sidecar (the original export is never modified)
- **Telemetry video overlay** — configure which telemetry lanes appear over the footage, locked to the same playhead, markers, sprint window, and units as the charts
- **Video export** — export the trimmed, overlaid clip as H.264 MP4 or QuickTime, with explicit resolution, frame-rate, and bitrate control
- **Chart export** — export stacked charts as PNG or JPEG, with a dark or white background, optional sprint info (distance, reaction time, steps, weather), a live preview, and a Falcatarun.com + date attribution stamp
- **CSV export** — export selected chart lanes and sprint info, with optional markers and foot strikes, delimiter selection, and a live preview
- **Standalone video analysis** — open any video without a linked sprint and mark Start / Finish / Distance points to read velocity and acceleration from the footage alone (the same marker-based method as the web analyzer)
- **Team Roster** — organize athletes and assign their sprint sessions and videos, so a coach can manage a whole squad from a single library; sessions can be moved between athletes or left unassigned
- **AI Sprint Coach (optional)** — coaching grounded in your measured numbers, plus a chat that answers questions across your whole imported sprint history. Run it fully on device with Apple Intelligence or a local open model, or bring your own cloud API key (Anthropic, OpenAI, OpenRouter). On-device providers keep your data on your Mac; any cloud use is opt-in behind a clear consent

## Web analyzer (browser — app.falcatarun.com)

A free, install-free companion that runs entirely in the browser at **[app.falcatarun.com](https://app.falcatarun.com)**. It needs nothing but a video — no Apple Watch, no account, no upload — and brings Falcata's marker-based video analysis to any device and any sprint footage.

- **Local video, frame-accurate** — open a clip from your device and scrub it frame by frame; nothing is uploaded
- **Distance markers** — place Start / Distance / Finish points on the timeline; Start is always 0 m and there is one Start and one Finish per clip
- **Ground contact time (GCT) markers** — mark contact → toe-off spans to read each step's GCT in milliseconds
- **Sprint-window validation** — markers before Start or after Finish are flagged out of bounds; a Start marker sets t = 0 for sprint-relative time
- **Velocity, acceleration & sprint stats** — average velocity per segment, launch acceleration from the Start, and a sprint summary (duration, max average speed, start acceleration), all computed from your markers
- **WYSIWYG overlay** — a live, configurable overlay (time, velocity, acceleration, GCT, sprint stats, video name) drawn exactly as it will export
- **Export** — a PNG still, a short sprint-window video clip (WebM / MP4, with the source audio), or a CSV of markers and velocity / acceleration / GCT segments (SI columns)
- **Metric or imperial** display units, remembered per video
- **Local catalogue** — markers, playhead, and units auto-save per video file in the browser (IndexedDB); reopening the same file restores your work. Video bytes are never stored
- **AI Vision (on-device pose analysis)** — run AI on any marked section to trace a frame-by-frame skeleton (blue bones, neon-green joints), detect each foot strike and time ground contact automatically (read-only AI GCT bars), count contacts split left/right, and flag overstriding (foot landing ahead of the body, possible/likely severity). The model runs entirely in the browser — no upload — and results persist per video file; V1 analyzes one section at a time and blocks sections longer than 30 seconds. This is computer-vision pose analysis, distinct from the LLM-based AI Sprint Coach, which remains a macOS-Analyzer feature
- **Privacy** — videos are processed locally and never uploaded; only a strictly opt-in, consent-gated analytics cookie is used (decline and nothing is sent)

It complements Falcata Analyzer on the Mac: the Mac app overlays measured Watch telemetry on your footage and is best for full-session review, while the web analyzer needs only the video and your markers and is ideal for quick, shareable splits and ground-contact analysis on any clip.

## Roadmap

- **Video-first sprint review** — continue improving Start Line Camera capture, sync, and overlay validation against real footage
- **Honest signal processing** — keep step detection, acceleration, GCT, and sprint-end logic tied to shared app processors instead of duplicate paths
- **Workflow clarity** — make it obvious when the iPhone can record the start only, finish only, or the full sprint
- **AI coaching (Analyzer, opt-in)** — Falcata Analyzer on macOS now has an AI Sprint Coach: on device (Apple Intelligence or a local open model) or bring-your-own-key cloud. The iPhone and Watch stay focused on measured biomechanics, reliable camera evidence, and transparent metrics — AI is never required, and nothing leaves your Mac unless you opt into a cloud provider
- **AI Vision (Web Analyzer, on-device)** — the browser app now runs on-device pose analysis on a marked section (skeleton overlay, automatic ground contact, foot-strike counts, overstride flags) with no upload — distinct from the macOS AI Sprint Coach

## Data and sync

- **Watch-to-iPhone sync** via WatchConnectivity file transfer with ack-based retry queue
- **iCloud Drive backup** for session metadata and compressed curve files
- **HealthKit iCloud sync** as a secondary delivery path
- **Lazy migration** — older sprints automatically updated when the algorithms improve

## Privacy

- Your data stays on your devices and in your own iCloud account
- No third-party analytics servers processing your motion data
- HealthKit integration is optional

---

Learn more at [falcatarun.com](https://falcatarun.com).
