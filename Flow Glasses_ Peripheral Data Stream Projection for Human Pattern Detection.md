Flow Glasses: Peripheral Data Stream Projection for Human Pattern
Detection

Author: Eric Don McElroy

Date: 2026-06-10

Contact: Knoxville, TN

Version: 1.0 -- Public Release / Prior Art Disclosure

\-\--

Abstract

Humans are exceptionally sensitive to motion, edge changes, and flow
discontinuities in peripheral vision -- a survival trait evolved to
detect predators. This paper describes Flow Glasses, a wearable device
that projects real‑time, multi‑dimensional data streams as flowing
textures into the wearer\'s peripheral field. No symbols, no numbers, no
translation. The brain passively detects anomalies (hiccups) in the
flow, then directs focused attention to investigate. The device acts as
a bidirectional human‑machine interface without neural implants: the
machine shows data as motion, the human responds with gaze direction and
micro‑expressions captured by integrated eye tracking. Off‑the‑shelf
components, buildable today.

\-\--

Problem Statement -- The Translation Bottleneck

Current Method Problem

Dashboards, graphs, text Requires focused attention, symbolic decoding,
slow.

Alarms & alerts High false‑positive rate, desensitization.

AI summarization Filtered by machine, misses unknown unknowns.

Humans perceive motion in peripheral vision at 100--200 ms latency,
without conscious effort. Yet almost all data interfaces are foveal
(central) and symbolic. This discards a massive biological compute
resource.

\-\--

Concept Overview -- Fluid Dynamics on Glass

The Flow Glasses consist of:

1\. Transparent OLED or waveguide display (e.g., Vuzix Shield, HoloLens
2, or low‑cost DIY using micro‑projectors). Displays only moving
textures -- no text, no graphs.

2\. Eye tracking camera (integrated in glasses frame, 60--120 Hz).
Detects where the wearer looks.

3\. IMU (gyro/accelerometer) to cancel head motion from perceived flow.

4\. Small compute unit (Raspberry Pi 5 or smartphone) that:

· Receives real‑time data streams (sensor feeds, AI predictions, system
logs).

· Renders the data as a vector field -- each data variable becomes a
flow direction and velocity.

· Maps the field onto the peripheral visual field (20--60° from center).
Central 20° remains transparent or dim.

· Runs at 60+ fps to mimic natural motion.

User experience: Wearer looks straight ahead, sees a seamless moving
texture in their periphery -- like looking out a window while rain flows
across the glass. If all data is normal, flow is smooth. If an anomaly
occurs (sensor spike, prediction error, system hiccup), the flow locally
stutters, swirls, or changes color/texture. The wearer\'s peripheral
vision detects the glitch instantly, without asking \"what does this
mean?\" The wearer then looks toward the glitch. Eye tracking logs the
moment and location, and the machine can zoom in on that data dimension
for further analysis.

\-\--

Off‑the‑Shelf Components (2026)

Component Example Cost (new)

Transparent display Vuzix Shield (developer kit) \$1,000

Eye tracking camera Pupil Labs Invisible (add‑on) \$500

Compute unit Raspberry Pi 5 8GB \$80

IMU BNO085 breakout \$30

Software Python + OpenCV + custom rendering \$0

Total \~\$1,610 (lower with DIY micro‑projector)

Mass production cost estimate (scaled): \$150--300 per unit.

\-\--

How It Works -- The Flow Rendering Pipeline

Step 1 -- Data to Vector Field

· Each monitored variable (temperature, CPU load, social token rate,
plasma stability) is assigned a base flow direction (e.g., temperature
increase → flow left to right).

· Instantaneous value determines flow velocity at that point in the
field.

· Multiple variables are overlaid as vector addition (flows add or
cancel).

Step 2 -- Field to Texture

· The combined vector field drives a moving noise texture (Perlin or
simplex noise). The texture moves in the direction and speed of the
local vector.

· Result: The wearer sees \"silk flowing over glass\" -- smooth when
stable, turbulent when variables change quickly or conflict.

Step 3 -- Anomaly Detection (Biological)

· The human visual system is exquisitely sensitive to divergence, curl,
and shear in moving textures.

· A hiccup (e.g., a sensor reporting a value 10× normal) creates a local
divergence -- the flow appears to \"sink\" or \"source.\" The wearer\'s
peripheral vision instantly registers it as a glitch.

· No training required. The brain already knows how to see a broken
flow.

Step 4 -- Interaction Loop

· Wearer detects glitch, glances toward it (saccade).

· Eye tracking captures the glance direction and timestamp.

· Machine maps that direction back to the data variable(s) that caused
the flow anomaly.

· Machine logs the event: \"Human detected anomaly in variable X at time
T.\"

· Machine can then query the wearer (via bone conduction earphone):
\"Investigate?\" Wearer nods or blinks (also tracked).

Result: The human becomes a peripheral anomaly detector for the machine.
The machine becomes a foveal tool for the human. Bidirectional,
non‑zero‑sum.

\-\--

Use Cases (Practical, Today)

Domain Data Streams Anomaly Example

Server room monitoring CPU temp, fan RPM, network latency A fan fails →
flow hiccups in lower left periphery → admin looks → solves.

Plasma channel steering Magnetic field strength, laser phase, particle
density Field gradient spike → swirl in peripheral → operator corrects
before disruption.

Medical ICU Heart rate, BP, O2 sat, IV drip Sudden BP drop → flow shear
→ nurse glances at correct monitor.

Colony pressure regulator HRV, social tokens, task completion Social
token drop → flow stagnation → colony manager initiates team event.

\-\--

Limitations & Mitigations

Limitation Mitigation

Peripheral motion can be distracting for some users Adjustable
brightness, opacity, and edge distance (30°--70°). Off switch.

Requires training to map glitch to action Use in parallel with standard
interface for 2--3 days. Brain adapts rapidly.

Eye tracking requires calibration Auto‑calibration every 10 minutes via
pupil detection.

Rendering lag \>30 ms breaks natural flow perception Use dedicated GPU
(even Raspberry Pi 5 can do 60 fps for 2D vector fields).

\-\--

Why This Is \"Injecting the Human into the Machine\"

No wires. No surgery. No symbolic translation. The machine presents its
internal state as a natural motion field -- something the human brain
already knows how to parse. The human responds with natural gaze
behavior -- something the machine can easily parse. The interface is the
peripheral vision.

The human becomes a sensor: \"There is a glitch somewhere over there.\"
The machine becomes an actuator: \"That glitch corresponds to variable
#142.\" Together, they detect anomalies that neither could find alone.
That is the injection.

\-\--

Development Path (Buildable in 3 Months)

1\. Week 1--2: Assemble glasses + eye tracking + Pi. Render simple test
patterns (uniform flow, vortex, sink).

2\. Week 3--4: Connect to one data stream (e.g., CPU temperature on a
local server). User study: does peripheral glitch detection exceed
chance?

3\. Week 5--6: Add multiple streams (temp, fan, network). Develop vector
overlay algorithm.

4\. Week 7--8: Integrate with existing monitoring dashboard. Run
parallel with screen for validation.

5\. Week 9--12: Package as a software‑only SDK for existing AR glasses
(HoloLens, Magic Leap). Publish reference design for DIY.

\-\--

Conclusion

The Flow Glasses turn the human peripheral nervous system into a
high‑bandwidth anomaly detector for machine data. Using only
off‑the‑shelf displays, eye tracking, and a vector field renderer, they
create a bidirectional non‑zero‑sum interface: machine shows data as
motion, human shows attention as gaze. No translation. No training. Just
flows and hiccups. Build it.

\-\--

This document is released to the public domain. No patent claimed. Go
make the glasses.
