White Paper: Project Superman -- A Distributed, Solid‑Fuel Pulse
Detonation Array for Personal Flight

Authors: Eric McElroy & Knox Makers Collective (concept)

Date: 2026-06-12

Status: Public Prior Art / Open Build Blueprint

Inspiration: Superman -- arms‑forward, prone flight, intuitive control

\-\--

1\. Executive Summary

Project Superman designs a wearable, multi‑engine flight suit that uses
solid calcium carbide and dry water to generate low‑pressure acetylene,
burned in an array of small pulse detonation tubes. Each tube is
independent, with its own screw feeder, Tesla‑valve intake, and nozzle.
Thrust vectoring is achieved by varying fuel feed per tube -- no
gimbals, no moving nozzles. The suit launches from a ground rig
(catapult or rocket assist), cruises at 30--70 mph for 20--30 minutes,
and lands via parachute or a small electric hover fan. The system is
inherently fail‑safe through redundancy: loss of any engine leaves
control intact.

\-\--

2\. Name

SUPERMAN'S VOLITION

(Volition = willpower, choice, self‑direction -- exactly how the pilot
flies)

\-\--

3\. Core Architecture

· 10--20 independent detonation tubes mounted on a rigid backplate with
spinal/neck support.

· Single hopper for mixed calcium carbide powder + dry water
(silica‑encapsulated water).

· Per‑tube screw feeder (stepper motor + auger) -- meters solid mix into
a tiny reaction chamber at tube inlet.

· Reaction chamber: water from dry water contacts carbide, producing
acetylene + steam + lime. No long gas lines -- acetylene generated right
at the tube.

· Tesla‑valve intake (fixed geometry) -- allows forward air to enter but
blocks reverse flow during detonation.

· Detonation tube (2--3 cm diameter, 20--30 cm long, Inconel or
ceramic‑lined steel).

· Ignition: low‑voltage phase‑change trigger or miniature spark
(stun‑gun style).

· Nozzle with heat recovery shroud: wraps exhaust nozzle, preheats
incoming air via annular passage. Optional thermoelectric generators
(TEGs) on shroud to charge onboard battery.

· Electronics: per‑tube microcontroller (or central ECU) controlling
screw speed and ignition timing. Sensors: IMU, barometer, airspeed
pitot, tube pressure/temperature, camera for pose estimation (fist
pointing).

· Control loops: simple PID for attitude stabilization using
differential thrust. AI (neural net on a small Jetson or Raspberry Pi)
for adaptive mapping between pilot's body position and desired thrust
vector.

\-\--

4\. Machines Required to Build (Knox Makers Shop List)

Machine Purpose Estimated Cost (new/used)

Metal lathe (e.g., 12x36) Turn tube sections, nozzle cones, intake
adapters \$3,000 -- \$8,000

Milling machine (vertical, CNC or manual) Machine backplate, motor
mounts, screw feeder housings \$4,000 -- \$15,000

3D printer (high‑temp, e.g., Voron with enclosed chamber, capable of
PEEK/ULTEM) Print Tesla valve prototypes, intakes, non‑structural parts
\$2,000 -- \$6,000

Sheet metal brake & shear Fabricate heat recovery shrouds, mounting
brackets \$500 -- \$2,000

TIG welder (for Inconel/steel) Assemble tube assemblies, reactor
chambers \$1,000 -- \$3,000

Bench grinder & belt sander Deburring, finishing edges \$200 -- \$500

Small parts cleaning station (ultrasonic) Clean lime deposits from test
parts \$100 -- \$300

Electronics workbench (oscilloscope, logic analyzer, soldering) Assemble
control boards, test sensor circuits \$1,000 -- \$3,000

Total machine investment (if buying new, minimal shop): \~\$12,000 --
\$40,000.

Knox Makers already has much of this -- the team would use existing
member‑owned tools.

\-\--

5\. Testing Stages (from bench to flight)

Stage 0 -- Material Safety & Handling

· Goal: Verify calcium carbide + dry water reaction rate, lime disposal,
acetylene stability at low pressure.

· Method: Bench reactor with pressure transducer, gas chromatograph
(rent).

· Success: Controllable gas flow, no clogging for 10 minutes continuous.

Stage 1 -- Single Tube Static Firing (No Forward Air)

· Rig: Tube with Tesla intake open to atmosphere, screw feeder, igniter,
thrust load cell.

· Test: Fire tube at various screw speeds, measure thrust, fuel
consumption, tube temp, detonation frequency.

· Success: Net positive thrust ≥ 2 N per cm² of tube cross‑section.

Stage 2 -- Single Tube with Simulated Forward Air

· Add: Leaf blower or wind tunnel (homemade duct) to push air into
intake at 30--50 mph.

· Test: Same as Stage 1, but varied airspeed. Measure thrust gain.

· Success: Thrust increases by ≥20% compared to static.

Stage 3 -- Heat Recovery Shroud on Single Tube

· Add: Annular shroud around nozzle, connected to intake preheat
passage.

· Test: Compare thrust and tube temp with/without shroud. If TEGs added,
measure electrical output.

· Success: Measurable thrust increase (≥5%) or TEG powers control
electronics.

Stage 4 -- Small Array (4 Tubes) on Ground Test Stand

· Build: 4 tubes in a square pattern, each with independent screw
feeder, common hopper.

· Control: Simple microcontroller varying each screw speed.

· Test: Measure net thrust vectoring by differential fueling. Verify
yaw/pitch authority.

· Success: Thrust vector control without moving parts.

Stage 5 -- Tethered Human Prototype

· Mount: Array on rigid backplate, worn by a pilot (safety harness,
helmet, parachute).

· Test: Suspended from a gantry or crane, tethered to prevent fall. Fire
engines, check control response, heat shielding, noise.

· Success: Pilot can command pitch/roll via body movement or joystick;
no burn injuries.

Stage 6 -- Ground Launch & Free Flight (Low Altitude)

· Launch rig: Catapult (bungee or pneumatic) providing 30--50 mph
initial speed. Or small solid rocket booster (JATO) that detaches.

· Flight: Over water or empty desert, altitude ≤ 50 ft, chase vehicle.
Pilot uses manual override. Parachute mandatory.

· Success: Controlled flight for 1 minute, safe landing.

Stage 7 -- Full System with AI & Sensors

· Add: Cameras (Intel RealSense or simple stereo), IMU, barometer, GPS,
pitot tube.

· AI training: Collect flight data in simulation (e.g., Gazebo + custom
PDE model). Then fine‑tune on real test flights.

· Control law: AI maps pilot's fist direction and body lean to desired
thrust vector, while envelope protection prevents stall/overspeed.

· Success: Hands‑free Superman pose steering for full flight duration.

\-\--

6\. Estimated Total Cost (Prototype to First Free Flight)

Phase Description Cost (USD)

0 Safety & chemistry testing \$500 -- \$2,000

1 Single tube static rig \$2,000 -- \$5,000

2 Wind tunnel/leaf blower \$200 -- \$1,000

3 Heat recovery shroud + TEGs \$500 -- \$1,500

4 4‑tube array & controller \$3,000 -- \$8,000

5 Tethered human rig & safety \$2,000 -- \$5,000

6 Catapult/rocket launch & flight test \$3,000 -- \$10,000

7 AI sensors, cameras, compute \$1,000 -- \$3,000

Contingency (30%) \$3,500 -- \$10,500

Total \$15,700 -- \$46,000

This is a makerspace budget -- professional aerospace development would
be 100x more.

\-\--

7\. Compute & Sensor Requirements

Onboard compute:

· Main flight controller: Pixhawk or similar (STM32) -- handles sensor
fusion, attitude control, failsafe.

· AI co‑processor: NVIDIA Jetson Orin Nano (or Raspberry Pi 5 +
Hailo‑8L) -- runs pose estimation (MediaPipe) and thrust mapping.

· Per‑tube microcontrollers: ATtiny or ESP32 -- control screw stepper,
ignition, report tube status via CAN bus.

Sensors:

· IMU (ICM-20948 or similar) -- 9‑DOF for attitude.

· Barometer (BMP390) -- altitude, climb rate.

· Pitot tube + pressure sensor (MPXV7002) -- airspeed.

· GPS (u-blox M10) -- ground speed, position.

· Thermocouples (Type K) on each tube -- temperature monitoring.

· Pressure transducers (MPX4250) in each tube -- detonation detection.

· Camera (Intel RealSense D435 or stereo webcam) -- pilot pose (fist
direction, body lean).

AI's role:

· Map camera skeleton + IMU to desired thrust vector (learned via
reinforcement learning in simulation).

· Predict tube misfires by analyzing pressure trace patterns -- skip
that tube before it damages.

· Adapt fuel mapping for altitude, air density, battery state.

Latency requirement: \<50 ms from pilot pose change to thrust change.
Achievable with edge AI.

\-\--

8\. Safety & Failsafe (Built In)

· Redundancy: 20 tubes for 15 needed -- lose 5, still fly.

· Burst discs: each tube vents overpressure away from pilot.

· Physical shielding between tubes -- a single rupture won't chain.

· Parachute (ballistic, rocket‑deployed) -- manual and auto (if altitude
loss \>10 m/s).

· Fuel cut‑off: screw feeders stop instantly; remaining acetylene burns
out in \<0.1 sec.

· Manual override: two joysticks on chest harness -- AI disabled, pilot
commands raw differential thrust.

· Emergency battery (Li‑ion, 100 Wh) -- powers sensors and parachute
deployment even if TEGs fail.

\-\--

9\. Open Questions / Gaps for the Team

1\. Tesla valve performance at 100 Hz detonation -- needs CFD or
cold‑flow test.

2\. Lime (Ca(OH)₂) accumulation -- will dry water's silica keep it
fluid? Test with simple reactor.

3\. Ground launch catapult -- pneumatic or elastic? Must accelerate 120
kg to 30 mph in 2 seconds (≈2.7g). Doable with 20 m rail.

4\. Noise suppression -- 100+ dB from each tube. Helmet with active
noise cancellation? Earplugs mandatory.

5\. Legal test site -- Knox Makers could partner with a private airstrip
or remote desert area (Nevada?).

\-\--

10\. Call to Action

Knox Makers has the machines, the talent, and the audacity. Stage 1
(single tube static) can be built for under \$2,000 and 3 months of
weekend work. The white paper is open -- take it, criticize it, improve
it. Then build a tube, light it, and measure.

"I just want to point my fist at the sky and not fall." -- Eric McElroy

\-\--

End of White Paper -- Public Domain, Prior Art, No Patents.
