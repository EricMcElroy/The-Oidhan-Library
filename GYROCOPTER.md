GYROCOPTER

A VTOL aircraft that transitions from powered rotor lift to fixed-wing
flight by morphing its rotor from a flat disc into a locked, streamlined
wing shape using smart materials.

Metadata

· Author: Eric Don McElroy

· Date: 2026-06-08

· Contact: eric.mcelroy@gmail.com, https://substack.com/@eskamick

· Version: 1.0

· Status: Public Release / Prior Art Disclosure

\-\--

Abstract

The Gyrocopter is a conceptual vertical-takeoff-and-landing aircraft
that escapes the speed limitations of traditional autogyros by
reconfiguring its main rotor mid-flight. A dual-motor system provides
forward thrust while an actively powered rotor enables vertical lift.
Once airborne, the aircraft accelerates forward, tilting the rotor disc
like a helicopter. At a critical speed where fixed wings can sustain
flight, the rotor blades morph---flattening from a high-lift profile
into a low-drag, nearly flat shape using internal shape-memory alloy
wires---and lock into a fixed position aligned with the aircraft's
longitudinal axis. The aircraft then cruises as an airplane, the static
rotor presenting minimal resistance. The transformation is reversible
for landing. This paper outlines the actuation mechanism, structural
feasibility, and control strategy, placing the morphing locked-rotor
convertiplane concept into the public domain.

\-\--

Problem

Autogyros and helicopters suffer from a fundamental speed ceiling
imposed by rotor aerodynamics: retreating blade stall, advancing blade
compressibility, and drag divergence limit practical forward velocity.
Conventional fixed-wing aircraft, while fast, require runways or complex
tilt-rotor mechanisms. There is no existing personal-scale or
experimental aircraft that combines the simplicity of a gyrocopter's
autorotative safety with the cruise speed of an airplane, while also
offering pure VTOL without the weight and complexity of tiltrotors or
dedicated lift fans.

A machine is needed that can:

· Take off and land vertically from any pad or clearing,

· Accelerate rapidly to airplane cruise speeds,

· Lock the rotor into a low-drag configuration once wing-borne flight is
established,

· Reconfigure back to rotor-mode for landing,

· Use only two propulsion sources (lift rotor + pusher propeller) with
no separate tail rotor.

The Gyrocopter concept addresses this by morphing the rotor itself.

\-\--

Concept

The aircraft comprises a fuselage with stub wings, a rear-mounted pusher
propeller driven by a combustion or electric motor, and a large overhead
rotor. The rotor is powered during vertical flight via a mast-mounted
motor (electric or hydraulic) and features blades capable of reversible
shape change.

Vertical Takeoff (Rotor Powered):

The rotor spins under power to generate lift. The pusher propeller is
vectored (via a ducted yaw vane or differential tilt) to counteract main
rotor torque, eliminating a tail rotor. The aircraft rises vertically.

Transition to Forward Flight:

As altitude is gained, the pusher thrust increases and the rotor disc is
tilted forward, converting some lift into thrust. The aircraft
accelerates horizontally. The stub wings begin generating lift, reducing
demand on the rotor.

Rotor Morph and Lock:

At a pre-determined airspeed (where wings alone can support the
aircraft), the following sequence triggers:

1\. Rotor collective pitch is reduced to zero lift.

2\. Embedded shape-memory alloy (SMA) wire actuators---arranged in
parallel stages along each blade---are electrically activated, causing
them to contract.

3\. These contractions pull the blade's internal structure from a
cambered airfoil shape into a flat or symmetric low-drag profile. The
blade cross-section collapses down, resembling a thin plank.

4\. The rotor is indexed and locked into a stationary position aligned
fore-aft (or two blades swept back) via a hub lock mechanism.

5\. Rotor power disengages; the aircraft is now a pure fixed-wing
airplane.

Reversion:

For landing, the sequence reverses: hub unlocks, rotor spins up (using
motor or autorotation), SMA wires cool/re-extend (passive cooling,
shape-memory effect reversed by blade's inherent spring-back or a second
set of opposing wires), restoring the high-lift airfoil shape. The
aircraft slows, tilts rotor vertical, and descends to a vertical
landing.

\-\--

Feasibility

The concept rests on several existing or emerging technologies:

· Shape-Memory Alloys (SMA): Nitinol wires contract up to 4--5% of
length when heated above their transition temperature (60--100°C).
Staged wire arrays can produce large, controlled deformations. NASA has
tested SMA-actuated morphing flaps and variable-camber wings. The
required blade shape change from cambered airfoil to flat profile is
within the strain range if distributed along the blade chord.

· Locking Rotor Hub: Helicopters such as the Sikorsky X2 and S-97 Raider
slow their rotors, but the Gyrocopter takes this further---fully
stopping and locking the rotor. Mechanical locking pins or a spline
brake can secure the mast.

· Vectored Pusher for Anti-Torque: Ducted deflectors behind a pusher
prop, or a gimbaled propeller, can provide yaw control. The Dornier Do
32 and various tail-sitter designs have used differential thrust or
vanes to counter torque without a tail rotor.

· Stub Wings: Small fixed wings provide lift at modest airspeeds; many
gyrocopters already possess stub wings. For a 500 kg aircraft, a 6 m²
wing area can generate sufficient lift at 90--100 knots.

· Transition Aerodynamics: The tilting rotor while powered is
essentially a helicopter in transition. Existing helicopter models
(e.g., UH-60) do this routinely; no fundamental aerodynamic obstacles
exist for the powered phase.

Challenges are in the rapid shape morphing synchronization, hub lock
precision, and vibration management, not in physics.

\-\--

Challenges

1\. Blade Morphing Speed: The transition from airfoil to flat must
happen within seconds to avoid an unstable intermediate drag state. SMA
actuation can be fast with high current pulses, but cooling for the
reverse cycle may be slower. A hybrid approach (SMA for contraction,
spring-return for expansion) can ensure timely reversion.

2\. Structural Integrity: Blades must withstand centrifugal loads while
containing internal actuators. A titanium or carbon-fiber spar with
SMA-articulated ribs and a flexible skin (elastomeric or morphing
composite) can bear loads.

3\. Aerodynamic Stability During Lock: As the rotor changes shape and
locks, the center of lift shifts abruptly. Fly-by-wire control of the
pusher thrust and tail surfaces (if any) must compensate automatically.

4\. Hub Lock Reliability: A partial engagement at speed could be
catastrophic. Redundant mechanical detents and magnetic locks can
provide fail-safes. The system can default to helicopter mode if lock
fails.

5\. Weight and Complexity: SMA wires, power supply, and actuators add
mass. The concept is most viable at larger scales (manned or heavy UAV)
where the speed benefit outweighs the weight penalty.

\-\--

Development Path

1\. Phase 1 -- Blade Segment Bench Test: Build a single blade section
with internal SMA wire arrays and morph it between airfoil and flat.
Measure force, speed, and cycle life.

2\. Phase 2 -- Whirl Rig Test: Mount a full morphing blade on a rotor
test stand. Spin under power, command shape changes, and measure
aerodynamic loading and vibration.

3\. Phase 3 -- Subscale UAV: Build a small-scale unmanned Gyrocopter
(2--3 m rotor diameter) with electric motors. Demonstrate vertical
takeoff, transition, rotor lock, and reversion in flight.

4\. Phase 4 -- Manned Prototype: Scale to a single-seat experimental
aircraft. Extensive ground testing, tethered hover, then incremental
transition with manual override.

5\. Phase 5 -- Public Release: Open-source all results, control laws,
and actuator designs. The Gyrocopter becomes a community-owned
configuration.

\-\--

Technology Stack

Component Example Tech

Rotor Blades Carbon-fiber spar, titanium ribs, silicone skin; embedded
0.5 mm Nitinol SMA wires in parallel stages

Rotor Hub Locking pin mechanism with centrifugal safety detent; electric
or hydraulic collective pitch

Pusher Propeller Variable-pitch pusher prop with ducted yaw vanes or
gimbaled mount for anti-torque vectoring

Forward Thrust Motor Turbocharged rotary engine (e.g., Rotax 915) or
high-power electric motor (e.g., Yasa P400)

Rotor Motor (VTOL) Direct-drive brushless DC motor (e.g., EMRAX 268) or
accessory hydraulic motor fed from main engine

Flight Controller Triple-redundant Pixhawk or custom FCS with transition
logic and rotor lock state machine

Sensor Suite IMU, GPS, pitot-static, angle-of-attack vane, blade strain
gauges, and rotor position encoders

Actuation Power Dedicated Li-Po battery for SMA heaters; separate
avionics battery

Airframe Composite monocoque with integrated stub wings and tail
empennage

\-\--

Author Note

This is theoretical. No prototype exists, no wind tunnel has validated
the morphing locked-rotor idea, and I'm not claiming a working aircraft
is hidden away somewhere. What I am doing is publishing the
concept---the combination of shape-memory alloy blade morphing, a
locking rotor hub, and a pure airplane cruise mode---so that it's free.
If it works, it could be the fastest autogyro ever imagined and a
genuinely useful VTOL machine. The materials to test it are available
now. Somebody with a workshop and a death wish for conventional
aerodynamics should try it.
