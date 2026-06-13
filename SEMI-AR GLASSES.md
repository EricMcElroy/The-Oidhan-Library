SEMI-AR GLASSES

Lightweight Glasses using layered light-pipes and peripheral LED arrays
to inject motion cues, directional prompts, and alerts into the user's
peripheral vision without screens, without overloading the visual
cortex.

Metadata

· Author: Eric Don McElroy

· Date: 2026-06-08

· Contact: eric.mcelroy@gmail.com, https://substack.com/@eskamick

· Version: 1.0

· Status: Public Release / Prior Art Disclosure

\-\--

Abstract

The Semi-AR Glasses are a non-screen augmented reality device that
communicates through the human peripheral vision system. Instead of
projecting heads-up displays onto the lens center, multiple transparent
light-pipe layers are stacked within the lens material and surrounded by
edge-mounted RGB LEDs. Selectively pulsing these LEDs creates motion
illusions, directional sweeps, color codes, and simple shapes that the
brain processes pre-attentively---before conscious recognition. A single
small reticle etched into the inner lens surface provides a centering
reference for AI camera alignment. The result is a minimalist,
low-cognitive-load information channel that can guide a user toward
threats, navigation waypoints, or AI-detected objects of interest, using
the visual instincts we already have rather than demanding focused
reading. The device is disclosed here as prior art.

\-\--

Problem

Existing augmented reality glasses face three persistent obstacles: they
place synthetic imagery directly in the center of vision, competing with
real-world scene processing; they are heavy, hot, and power-hungry due
to full-display engines; and they require the user to "read"
interfaces---a cognitively expensive task that breaks situational
awareness.

Human peripheral vision, in contrast, is exquisitely tuned to motion
onset, flicker, color change, and looming---abilities hardwired by
evolution for survival. Yet no commercial device exploits this channel
as a primary data conduit. There is a gap for a device that is:

· Lightweight enough for all-day wear,

· Power-sipping enough to run on a coin cell,

· Invisible in its operation (no glowing screens),

· And capable of delivering rich spatial information solely through
peripheral light patterns.

The Semi-AR Glasses fill that gap.

\-\--

Concept

The lenses are constructed as a laminate of multiple thin, transparent
layers (acrylic, polycarbonate, or glass) with slightly differing
refractive indices and internal optical boundaries. Each layer acts as a
discrete light pipe. Around the perimeter of the lens are micro-RGB
LEDs, each optically coupled to specific layers via miniature prisms
that compress the edge-light path to keep the frame thin.

· Layer Stacking & Prism Injection: Light from an LED enters a coupling
prism, which compresses its vertical profile and injects it into a
specific layer. Total internal reflection confines the light within that
layer until it strikes an etched feature, scattering it toward the
wearer's eye. Different layers can carry different signals
simultaneously without crosstalk.

· Etched References: On the innermost surface (closest to the eye), a
subtle, nearly invisible etched reticle---a simple dot or
crosshair---glows when back-illuminated by a dedicated layer. This marks
the AI's center of visual attention, aligning the user's gaze with the
system's camera without a screen.

· Peripheral Illusion Generation: By sequencing LED pulses---light
moving along the lens edge, shifting colors, or strobing in particular
spatial patterns---the glasses create apparent motion across the
wearer's peripheral field. For example:

· A left-to-right traveling wave along the top edge says "look right."

· A red pulse on the left edge warns of something entering from that
side.

· A gentle cyan sweep from bottom to top suggests ascent or "go up."

· Color fading and speed modulation can encode urgency or distance.

The system never places a blocking image in the center. All information
rides on the edges of perception, using the brain's own orientation
reflexes to guide attention without demanding it.

\-\--

Feasibility

The technological elements already exist, though not previously combined
for this purpose:

· Light-Pipe Layers: Multi-layer light guide displays have been
demonstrated by Lumus and Vuzix. Automotive head-up displays use
edge-lit acrylic sheets with laser-etched microstructures to produce 2D
symbols. Stacking two or three such layers with thin-film isolation is
well within current precision laminating capabilities.

· Prismatic Injection: Tiny injection-molded prisms (less than 1 mm
thick) can be attached to the lens edges to couple LED light into
specific layers. This is standard in edge-lit LCD backlights and thin
light guides.

· Micro-LEDs: RGB side-emitting LEDs in sizes down to 0.5×0.5 mm are
commercially available. Placing 20--50 around each lens provides
sufficient resolution for motion illusions, drawing only milliwatts when
activated individually or in small groups.

· Motion Perception: The human visual system perceives phi motion when
stationary lights flash in rapid succession. This principle is used in
LED signage and bicycle wheel lights. Reproducing it in a glasses form
factor requires only a microcontroller that can update LED states in the
100--200 Hz range.

· AI Integration: A miniature camera (e.g., at the bridge or temple)
feeds object detection to an edge-AI processor (ESP32-S3 or a TinyML
accelerator). The processor maps detected objects to directions and
commands peripheral light patterns via an LED driver matrix.

The entire system can be powered by a small Li-Po battery or a coin cell
for days due to the extremely low duty cycle of the LEDs.

\-\--

Challenges

1\. Layer Crosstalk: Light from one layer leaking into an adjacent layer
can produce ghost signals. Precision refractive index matching,
interstitial air gaps, or nanoscale photonic crystal barriers can
suppress crosstalk.

2\. Optical Clarity: Multiple layers may reduce see-through transmission
below 80%, particularly if adhesives yellow over time. Using UV-stable
polymers and anti-reflection coatings mitigates degradation.

3\. Universal Perception: Motion illusion effectiveness can vary between
individuals. A calibration mode where the user confirms perceived
direction can tune the timing and spatial pitch of LED sequences.

4\. Brightness vs. Ambient Light: In bright sunlight, peripheral pulses
may be washed out. High-intensity LEDs with dynamic current control and
automatic brightness sensing can compensate, but power draw increases.

5\. User Acceptance: Some wearers may find peripheral flicker irritating
or distracting. A gradual fade-in for alerts, user-adjustable intensity,
and a "do-not-disturb" mode can address this.

\-\--

Development Path

1\. Phase 1 -- Illusion Validation: Build a benchtop rig with a
single-layer acrylic sheet, edge-mounted LEDs, and a microcontroller.
Test different motion sequences with human subjects to map effective
speed, color, and pattern parameters for directional cueing.

2\. Phase 2 -- Multi-Layer Prototype: Laminate 2--3 thin acrylic layers
with different etch patterns. Verify independent layer control and
measure optical transmission. Test simultaneous illusions (e.g.,
top-layer motion + bottom-layer color pulse).

3\. Phase 3 -- Glasses Form Factor: Fit the layer stack into a standard
eyewear frame with embedded prism couplers and micro-LEDs. Wire to a
small driver board and battery. Conduct field tests in varied lighting.

4\. Phase 4 -- AI Integration: Add a low-power camera and edge processor
running a lightweight object-detection model (e.g., MobileNetV2).
Program real-time mapping of detected objects to peripheral light cues.
Test in navigation and situational-awareness scenarios.

5\. Phase 5 -- Public Release: Publish the full optical stack design,
PCB layouts, firmware, and user-study data. The Semi-AR Glasses concept
becomes public prior art.

\-\--

Technology Stack

Component Example Tech

Lens Layers Optical-grade PMMA (acrylic) or MR-8 polymer, 0.5--1 mm
each, with laser-etched microdots for light extraction

Prism Couplers Injection-molded Zeonex prisms (\<1 mm thickness)
optically bonded to lens edge

LEDs Side-emitting RGB micro-LEDs (e.g., OSRAM MicroSIDELED 0402),
mounted on a flex PCB hugging the frame

LED Driver LP5860T 18-channel RGB matrix driver, I²C controlled

Microcontroller ESP32-S3 for BLE connectivity and LED control, or
nRF52840 for ultra-low power

AI Processor (optional) TinyML accelerator (Himax WE-I Plus, \~1 mW)
running person/object detection

Power 40 mAh Li-Po cell, USB-C charging, target 3--5 days of normal use
between charges

Sensors Ambient light sensor (LTR-303), optional inertial IMU
(ICM-20948) for head tracking

Frame Standard acetate or titanium eyewear with embedded flex PCBs and
power

\-\--

Author Note

I'm not an optician, nor do I have a prototype in a drawer. This white
paper is a concept---a way to tap into the visual machinery humans
already possess, without screen addiction, without heads-up clutter. The
LEDs exist. The light pipes exist. The illusion tricks are older than
neon signs. What's new is putting them together in a pair of glasses
that whispers to your instincts instead of screaming for your attention.
If it works, you might walk through a crowd and just feel where to go,
without ever looking at a screen. That's worth a prototype. The
blueprint is now public.
