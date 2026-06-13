SUPERMAN HANG GLIDER

A hands-free, body-steered hang glider system that lets the pilot fly
like Superman, with AI-assisted counterweight control and full manual
override.

Metadata

· Author: Eric Don McElroy

· Date: 2026-06-08

· Contact: eric.mcelroy@gmail.com, https://substack.com/@eskamick

· Version: 1.0

· Status: Public Release / Prior Art Disclosure

\-\--

Abstract

The Superman Hang Glider replaces the traditional rigid control frame
with a chest-and-shoulder suspension rig that frees the pilot's arms and
allows the upper body to pivot freely. An AI-controlled counterweight
actuator on the bar handles automatic stabilization, while a
camera-based pose-estimation system enables the pilot to steer simply by
pointing a fist forward---flying like Superman. Twin fly-by-wire
joysticks provide manual control, and a mechanical detach system
instantly returns full authority to the pilot. Onboard envelope
protection prevents stall and overspeed, but a dedicated override allows
the pilot to push through any limit in an emergency. The system
integrates proven technologies already deployed in drones, active kite
systems, and modern fly-by-wire aircraft, making the concept immediately
buildable as an aftermarket kit or experimental ultralight.

\-\--

Problem

Conventional hang glider controls require the pilot to grip a rigid bar,
shifting body weight to steer. This ties up both hands, limits
upper-body freedom, and makes tasks like operating cameras, radios, or
sensors impossible without releasing a control surface. It also denies
an experience that millions have dreamed of: flying with arms
outstretched, steering by instinct, feeling like Superman.

There is a genuine human-factors and mission-utility gap for an
ultralight flight system that:

· Leaves both hands free during routine flight,

· Allows intuitive, body-driven steering,

· Retains the direct manual authority that pilots demand, and

· Is just absurdly cool to fly.

The Superman Hang Glider closes that gap by merging modern pose
estimation, active counterweight control, and a pilot-respecting
override philosophy into a single, buildable airframe.

\-\--

Concept

The glider replaces the standard harness-and-bar arrangement with a
chest/shoulder suspension that supports the pilot below the wing's
center of mass. A movable counterweight---driven by a linear actuator on
the bar---shifts the system's center of gravity under AI command,
providing pitch and roll authority.

Manual Mode (Fly-by-Wire):

Two small joysticks, mounted at the pilot's sides or on a short
armature, send commands to the actuator servos. The pilot flies using
light fingertip pressure, as in modern fly-by-wire aircraft. No grip
strength or arm endurance required.

Superman Mode:

A rigid mast rising from the bar places a wide-angle camera above and
slightly forward of the pilot. The pilot releases the joysticks, extends
one arm forward with a closed fist, and assumes a slight prone body
posture. An onboard processor running real-time 3D body-pose estimation
(e.g., MediaPipe or a stereo-depth + IMU fusion) interprets the angle of
the extended arm, torso orientation, and subtle shoulder shifts as
pitch, roll, and yaw inputs. Steering becomes as natural as pointing
where you want to go.

Safety & Reversion:

· The AI maintains a dynamic flight envelope (angle-of-attack, speed,
load factor) and prevents commands that would violate it.

· A guarded override switch allows the pilot to blow through any limit
when emergency demands it.

· A mechanical quick-release on the actuator linkage lets the pilot yank
a lever and immediately revert to pure weight-shift control---the bar
becomes a rigid bar again, and the pilot flies it old-school.

\-\--

Feasibility

All required subsystems exist as commercial off-the-shelf or proven
experimental technologies:

· 3D Pose Estimation: Lightweight stereo cameras coupled with IMUs and
neural-network pose estimators (OpenPose, MediaPipe, custom TinyML
models) can track arm and body orientation at 30+ fps on a low-power
embedded processor like an NVIDIA Jetson Nano or Xavier NX. Hand-gesture
drone control is already shipping in consumer products.

· Fly-by-Wire Actuation: High-torque, fast-response linear actuators
(ball-screw or belt-driven) used in active kite control (Makani,
kiteboat steering) and UAV load-shift systems can reposition a 15--25 kg
counterweight over the required range in under 200 ms.

· Flight Envelope Protection: Compact angle-of-attack vanes,
pitot-static tubes, and GPS modules (used on paramotors and UAVs) feed
an air-data computer that enforces limits. The architecture mirrors
commercial envelope protection logic from glass-cockpit GA aircraft.

· Manual Reversion: A sprung clutch or shear-pin linkage between the
actuator and the bar, combined with a pilot-operated disconnect lever,
provides a fail-safe mechanical bypass. This is standard practice in
power-steering and fly-by-wire systems with manual reversion
requirements.

· Power: A lithium-polymer battery pack sized for 2--4 hours of
actuation and avionics, recharged between flights.

Integration risk is low; the primary challenge is tuning the control
algorithms and ensuring the pose estimator works reliably across
lighting conditions and pilot body types.

\-\--

Challenges

1\. Weight and CG Budget: The actuator, counterweight, battery, and mast
add mass that must be offset by a larger wing or reduced pilot mass. A
lightweight counterweight system (shifting the pilot's own suspension
point rather than a dead mass) can mitigate this.

2\. Pose Estimation Robustness: Variable lighting, glint, and fast body
motion can confuse pure-vision systems. Redundant sensing (IMU on
pilot's chest strap + magnetic tracking) can fuse with vision.

3\. Latency: From fist movement to actuator response must be under \~150
ms to feel telepathic. Actuator bandwidth and processor pipeline must be
sized accordingly.

4\. Human-Factors of Override: Pilots may forget or hesitate to use the
manual reversion. Training and unambiguous tactile feedback on the bar's
state (e.g., a change in resistance) are essential.

5\. Certification: Any aftermarket kit for existing hang gliders or a
new ultralight design will face regulatory scrutiny. The system is
disclosed here as prior art to ensure the underlying concept remains
open and unencumbered.

\-\--

Development Path

1\. Phase 1 -- Simulation & Bench Testing: Build a full control loop in
a flight simulator with a mockup harness and body-tracking camera to
validate pose-to-steering translation and envelope protection logic.

2\. Phase 2 -- Ground Rig: Install the actuator and counterweight on a
static rig with a pilot suspended, tune response, and conduct
human-factors evaluations of the emergency disconnect.

3\. Phase 3 -- Small-Scale UAV: Mount a scaled version on a large RC
paraglider or kite to validate sensor fusion and control algorithms in
real air before risking a human.

4\. Phase 4 -- Full-Scale Prototype: Adapt an existing hang glider
(e.g., Wills Wing Falcon) with the full system. Initial flights tethered
or with a chase vehicle, then free flight with gradual envelope
expansion.

5\. Phase 5 -- Community Release: Open-source the mechanical,
electrical, and software designs. The first pilot to pull off a
sustained Superman pose in flight earns serious bragging rights.

\-\--

Technology Stack

Component Example Tech

Body Pose Estimation Stereo camera (Intel RealSense D435i), 9-DOF IMU on
chest strap, MediaPipe Pose or custom CNN

Onboard Processor NVIDIA Jetson Orin Nano or Raspberry Pi 5 + Hailo-8L
AI accelerator

Flight Controller / Envelope Protection Pixhawk with custom ArduPilot
Lua scripts, pitot tube (Airspeed Sensor 4525DO), AoA vane

Counterweight Actuator LinMot linear motor or ballscrew with Maxon BLDC;
load cell for haptic feedback

Manual Fly-by-Wire Joysticks Dual 3-axis industrial joysticks (e.g.,
APEM XD Series) with CAN bus output

Emergency Disconnect Solenoid-actuated pin or manual Bowden cable
releasing actuator carriage from bar

Power System 14S Li-Po (6--8 Ah) for actuator, 5V/12V regulators for
avionics

Camera Mast Telescopic carbon-fiber pole, damped mount, with break-away
feature for crash safety

Software Architecture ROS2 nodes for sensor fusion, control filtering,
and redundant state machines; C++/Python

\-\--

Author Note

I'm not a pilot. I've never flown a hang glider, and I don't have a
prototype sitting on a workbench. This paper is an idea---a design
concept published as prior art to ensure the Superman Hang Glider
remains open, unencumbered, and available for anyone with the skills and
courage to build it. If the freedom to fly like that matters, it belongs
in the public domain. Somebody out there will strap in, point a fist at
the horizon, and make it real. I just wanted the blueprint to be free
when they do.
