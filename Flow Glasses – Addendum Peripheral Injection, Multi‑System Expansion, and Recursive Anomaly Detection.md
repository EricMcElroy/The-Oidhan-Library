Theoretical Addendum: Flow Glasses -- Peripheral Injection, Multi‑System
Expansion, and Recursive Anomaly Detection

Author: Eric Don McElroy

Date: 2026-06-10

Contact: Knoxville, TN

Version: 1.0 -- Public Release / Prior Art Disclosure

\-\--

A.1 Introduction

The Flow Glasses white paper describes a practical device that projects
data as peripheral motion, enabling the human visual system to detect
anomalies without symbolic translation. This addendum expands the
concept by exploiting secondary bleed‑off effects, connecting to the
Continuous Friction Planarization (CFP) mirror machine, and introducing
recursive anomaly loops. The glasses are not a standalone viewer -- they
are a node in a multi‑vector human‑machine friction interface.

\-\--

A.2 Exploitation of Peripheral Motion Bleed‑Off

The glasses project a moving texture. The human retina, optic nerve, and
visual cortex process this motion regardless of conscious intent.
Bleed‑off effects:

A.2.1 Saccadic Masking Exploitation

During rapid eye movements (saccades), visual sensitivity drops. The
glasses can inject sub‑saccadic pulses -- brief, high‑contrast flow
changes that occur during the saccade but are not consciously perceived.
The pulvinar nucleus (thalamus) still registers them. Result: subliminal
anomaly alerts that the user "just knows" without seeing a hiccup.

A.2.2 Optokinetic Nystagmus (OKN) Harvesting

OKN is the reflexive eye movement when following a moving pattern. The
glasses can generate a global flow drift that slowly shifts the user's
gaze toward a region of interest (e.g., a data anomaly). The user feels
a "pull" to look in a certain direction. No conscious command -- the
brain just orients.

A.2.3 Afterimage Persistence

A brief high‑velocity flow discontinuity leaves a short‑lived afterimage
on retinal ganglion cells. By carefully timing the anomaly, the glasses
create a faint, moving afterimage that persists for 100--200 ms after
the user looks away. This extends the anomaly detection window without
increasing frame rate.

\-\--

A.3 Connection to the CFP Mirror Machine

The CFP process produces optically flat metal mirrors. The Flow Glasses
require high‑quality transparent optics to avoid distorting peripheral
flow. Standard AR waveguides introduce chromatic aberration and
ghosting. CFP‑made mirrors solve this:

A.3.1 Ultra‑Flat Combiner Lenses

A CFP‑produced aluminum or copper mirror, when coated with a thin
dielectric, becomes a high‑reflectivity combiner. Stamped with a
micro‑scale Fresnel pattern (using the same friction master), it focuses
light without bulk glass. Flatness \<50 nm ensures no phase distortion
of projected motion.

A.3.2 Self‑Aligning Optical Path

The glasses' eye tracker can be mounted on a CFP‑fabricated reference
surface. The mirror's flatness ensures the eye tracker's coordinate
system aligns with the projection plane to sub‑pixel accuracy.
Calibration becomes a one‑time factory step.

A.3.3 In‑Situ Re‑Polishing

If the combiner scratches, a miniature CFP tool (a spinning, cooled
metal rod) can be built into the glasses frame. Run it across the mirror
surface for 2 seconds -- the scratch ablates away, and the mirror is
restored. Off‑the‑shelf micro‑motor and a diamond master. Glasses
self‑repair.

\-\--

A.4 Recursive Anomaly Loops -- The Human Becomes the Master

The base system: Machine shows flow → Human detects hiccup → Machine
logs variable. Recursive expansion:

A.4.1 Human‑Generated Anomalies

The user can intentionally create a flow hiccup by, for example,
thinking of a specific memory (detected via pupil dilation) or moving
their hand in front of the glasses (edge motion). The machine learns to
associate that intentional hiccup with a command: "Show me the last 5
minutes of data" or "Mark this moment for later review." The user trains
the machine using peripheral motion they generate.

A.4.2 Cross‑System Friction

The CFP machine's acoustic emission (from Section A.3 of the CFP
addendum) is fed directly into the Flow Glasses as a flow texture. A
sudden change in grinding sound (e.g., master wear) becomes a peripheral
swirl. The operator glances, sees the swirl, and knows to replace the
master without checking a screen. The mirror machine talks to the
glasses via a shared data bus.

A.4.3 Predictive Hiccup Generation

The machine models the user's past anomaly detections. When it predicts
a future anomaly (e.g., a temperature spike in 10 seconds), it
pre‑generates a forward‑propagated flow distortion that starts subtly
before the event. The user's peripheral vision sees a "pre‑echo" and can
take preemptive action. This turns the glasses into a predictive
peripheral display.

\-\--

A.5 Non‑Zero‑Sum Coupling with the Pressure Regulator

The Pressure Regulator (white paper) monitors HRV and social tokens to
balance coddling/pressure. The Flow Glasses can feed into that system:

· User's peripheral detection rate (anomalies caught per hour) is a
measure of cognitive load. High detection rate with many false positives
→ overpressure. Regulator triggers a comfort event.

· Low detection rate with long response latency → under‑coddling
(boredom, fatigue). Regulator introduces a challenge.

The glasses become a biometric sensor for the Regulator, without extra
hardware. The Regulator becomes an adaptive gain control for the glasses
(adjusts flow contrast, speed, and anomaly threshold).

\-\--

A.6 Vector Stacking -- Full Integrative Example

Scenario: A CFP mirror machine is running unattended. The operator wears
Flow Glasses and is also monitored by the Pressure Regulator.

1\. CFP acoustic emission detects high‑frequency chatter (master wear).

→ Glasses render a high‑frequency vibration texture in lower left
periphery.

→ Operator glances. Eye tracking logs the variable: "Master wear
anomaly."

2\. Regulator notes operator's HRV stable (good pressure balance).

→ No comfort/challenge override.

3\. Operator intentionally creates a blink‑pattern anomaly (three rapid
blinks).

→ Machine interprets as "Show me master wear trend over last hour."

→ Glasses render a flow that moves right‑to‑left at a speed proportional
to wear rate. Operator sees a slow drift → wear is mild.

4\. Machine predicts wear will reach critical in 15 minutes.

→ Glasses pre‑generate a faint, growing swirl in the same location.

→ Operator, before any alert, looks and initiates auto‑lapping cycle.

5\. During lapping, the CFP machine's triboelectric charge powers a
small LED.

→ Glasses detect the LED flicker (via ambient light sensor) and render
it as a confirmation texture.

→ Operator sees the loop close.

All five steps happen within 60 seconds. No alarms. No dashboards. The
human, machine, glasses, and regulator act as one distributed
sensing‑action system.

\-\--

A.7 Hardware Requirements (Off‑the‑Shelf)

Component For Glasses For CFP Integration

Eye tracking 60 Hz camera Same camera can monitor CFP mirror reflection

IMU BNO085 Same IMU detects CFP vibration (no extra sensor)

Acoustic pickup -- Already present in CFP addendum

Ambient light sensor \$5 photodiode Detects LED or plasma flashes

Shared data bus WiFi or serial Raspberry Pi bridges both systems

Total added cost \~\$10 (sensors) + software --

No new exotic parts. The integration is wiring and a few lines of code.

\-\--

A.8 Conclusion

The Flow Glasses, when expanded via secondary effects and coupled with
the CFP mirror machine and Pressure Regulator, become a unified
human‑machine friction interface. They exploit saccadic masking, OKN,
afterimages, and predictive hiccups to achieve bidirectional
communication without neural implants. They self‑repair using CFP
micro‑tools. They regulate operator state using the Regulator's HRV and
detection rate. And they turn every glance, blink, and peripheral glitch
into a non‑zero‑sum transaction.

This addendum closes the loop between the three core systems: glasses
(peripheral injection), CFP (physical shaping), and Regulator
(psychological balancing). They are not separate inventions. They are
legs of the same table.

Released to the public domain. Build the triad.
