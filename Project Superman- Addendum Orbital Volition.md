White Paper Addendum -- Project Superman: Orbital Volition

Closed-Loop Photonic Tether EVA Propulsion (Internal Design Study)

Authors: Eric McElroy & Knox Makers Collective

Date: 2026-06-12

Status: Internal / Not for Public Release

Classification: Prior Art -- No Patents

\`\`\`white-paper

White Paper Addendum -- Project Superman: Orbital Volition

Closed-Loop Photonic Tether EVA Propulsion (Internal Design Study)

Authors: Eric McElroy & Knox Makers Collective

Date: 2026-06-12

Status: Internal / Not for Public Release

Classification: Prior Art -- No Patents

\`\`\`

\-\--

1\. Addendum Purpose

This document supersedes the atmospheric solid‑fuel pulse‑detonation
array concept of the original Project Superman white paper for vacuum
operations. All chemical propulsion, combustion, mass ejection, and
solid‑fuel handling have been eliminated. The system described herein is
a fully closed‑loop, zero‑waste, electrically passive EVA mobility
solution that uses only a station‑based laser and two constant‑tension
tethers. The pilot flies free in a large volume near a base or vessel,
pushes against nothing but light, and retains complete 6‑DOF control via
body pose alone.

The core design constraint set forth by the team: no waste, no onboard
propellant, use what space gives us, keep the Superman pose intuitive.

\-\--

2\. System Name

ORBITAL VOLITION -- PHOTONIC TETHER ARRAY

Volition: self‑directed motion by will alone. Photonic: the sole impulse
source is momentum transfer from a laser. Tether Array: two
spring‑loaded lines that provide geometric constraint and regenerative
return, without any reliance on the tether for propulsion.

\-\--

3\. Core Architecture

The complete EVA system consists of three components:

1\. Station‑Side Laser & Tracking Unit

· A single diode‑pumped solid‑state or fibre laser (power class:
100--500 W continuous, visible or near‑IR).

· High‑resolution stereo camera array with AI‑based 6‑DOF pose
estimation (e.g., MediaPipe or a custom skeleton tracker) that
identifies retroreflective fiducial patches on the pilot's suit.

· Fast‑steering mirror or beam director to aim the laser spot onto any
desired point on the pilot's body with \<50 ms latency.

· Power draw from station's main bus; laser waste heat rejected via
existing station radiators.

2\. Twin Tether Assembly (Station Side)

· Two independent reels, each containing a high‑strength, low‑creep
tether (Dyneema or Vectran, 0.5--1.0 mm diameter) wound on a
constant‑force (negator) spring drum.

· Spring design maintains a constant, gentle tension of \~0.5--1.0 N per
tether regardless of payout length.

· Each reel includes a simple magnetic particle brake or eddy‑current
damper to prevent snap‑back, and an encoder to measure extended length
for the station's state estimation.

· Attachment points on the station are separated by 2--5 metres,
providing a wide baseline for three‑dimensional positioning.

3\. EVA Suit (Pilot Side)

· Standard IVA or light EVA pressure garment.

· Two attachment hard points (hip/shoulder rings) for the tethers,
arranged to keep the pilot's centre of mass within the tether triangle
without impeding limb movement.

· Suit exterior covered with an array of small, lightweight
retroreflective spheres or corner‑cube patches, distributed to ensure
the station's cameras can unambiguously determine full body pose from
any angle.

· No onboard thrusters, no batteries, no high‑voltage electronics. The
suit is completely passive in terms of propulsion.

· Optional: a thin, stiff backplate or "sail panel" of white Beta cloth
with embedded corner‑cube film to increase photon momentum coupling
(reflectivity \> 90%) where the laser is most likely to strike.

\-\--

4\. Operating Principle

4.1 Thrust Generation

Photons carry momentum p = E/c . A laser of power P reflecting from a
perfectly reflective surface delivers a force F = 2P/c along the beam
direction. At 500 W, that yields approximately 3.3 micronewtons -- tiny,
but continuous and lossless. In microgravity, even micronewtons
accelerate a 120 kg pilot‑suit system at \~0.03 mm/s². Over a 10‑minute
manoeuvre, that builds a displacement of \~5 metres and a velocity of
\~2 cm/s -- perfectly sufficient for deliberate, precise EVA motion near
a station where no rapid dashes are required.

The suit's sail area can be increased with a deployable reflective
parasol (e.g., a lightweight aluminised Kapton disc) to boost force, but
for most operations the bare suit surface is adequate.

4.2 Directional Control

The pilot simply assumes the classic Superman pose: one arm extended
forward, fist pointing toward the desired destination. The station's AI,
tracking the fiducial markers, interprets this vector and directs the
laser to strike the pilot's torso or a dedicated sail panel from an
angle that produces a net impulse along the indicated axis. For example:

· Pointing toward a worksite: laser pushes the pilot from behind,
accelerating them forward.

· Pointing back toward the station: the beam strikes the pilot's chest,
decelerating them (or, more often, the tethers' spring tension takes
over for return).

By rotating the torso or angling the arm, the pilot can request lateral
or vertical translation. The AI continuously solves for the beam
incidence angle that produces the desired thrust vector within the plane
defined by the two tether lines. The tether tension triangle naturally
constrains motion to a smooth, predictable surface, turning the pilot's
intent into a well‑defined trajectory.

4.3 Regenerative Braking & Return

When the pilot wishes to stop or return, they either:

· Present a "stop" gesture (open palm facing the station), causing the
laser to switch to a decelerating beam on the opposite side, or

· Simply relax and allow the constant‑tension tethers to reel them
gently back. The negator springs absorb the pilot's kinetic energy as
they retract, converting it into stored spring potential for the next
outward leg -- true mechanical energy recovery without any electrical
conversion losses.

Damping on the reels prevents oscillatory bouncing. The system naturally
comes to rest when the pilot is back near the airlock.

4.4 Safety & Fail‑Safe Design

· Laser shut‑off: if the tracking AI loses pose lock or the pilot exits
a pre‑defined safety volume, the laser instantly cuts.

· Tether integrity: two independent tethers provide redundancy. If one
fails, the other can still reel the pilot back.

· Spring‑loaded reels: in the event of complete power loss, the tethers
simply retract, bringing the pilot home passively.

· No hazardous materials: zero chemical energy, zero high pressure, zero
electrical shock risk on the suit. The pilot could cut the tethers and
become a free‑floating object without any immediate danger (though
standard EVA procedure would dictate retrieval).

\-\--

5\. Key Design Advantages

· Zero onboard consumables. No propellant, no coolant, no battery. The
suit never needs refuelling; only the station's laser and reels require
power and maintenance.

· Perfectly silent, cold operation. No combustion, no exhaust, no
vibration. The EVA experience is meditative, like swimming in stillness.

· Intuitive, embodied control. The Superman pose directly translates
body geometry into motion. No joysticks, no switches, no cognitive
mapping required. An astronaut's natural spatial awareness becomes the
flight controller.

· Scalable. Multiple pilots can operate simultaneously by sharing the
laser via time‑division multiplexing or by deploying separate tracking
units. Each pilot has their own tether pair.

· Minimal station infrastructure. The laser is a modified industrial
welding/cutting unit; the reels are simple mechanical devices; the AI
runs on existing station compute. Total mass and volume are negligible
compared to any propellant‑based EVA system.

· Closed‑loop energy. The tethers' springs recover kinetic energy; the
laser's waste heat is dumped via the station's radiators; no momentum is
exchanged with Earth's magnetic field or ionosphere -- this system
functions in deep space near any vessel, not just LEO.

\-\--

6\. Remaining Technical Challenges (Fiddly Bits)

1\. Laser‑body coupling efficiency. The suit's reflectance must be high
(\>0.9) across the laser wavelength to maximise force and minimise
heating. Corner‑cube retroreflectors may produce a return beam that
misses the station; a Lambertian white surface might be easier.

2\. Pose estimation accuracy. The AI must determine not just limb
positions but the exact orientation of the pilot's torso to project the
intended thrust vector. Machine‑vision fiducials on a wrinkled, moving
EVA suit in variable lighting are a known challenge; testing with a
suited mannequin in a vacuum chamber is the next step.

3\. Laser beam steering dynamics. A 500 W continuous‑wave beam must be
aimed with microradian precision and slewed across a 60‑degree cone at
rates up to a few degrees per second. Off‑the‑shelf galvanometer mirrors
may suffice.

4\. Spring‑tether dynamics. Long Dyneema lines in microgravity can
exhibit unexpected stick‑slip behaviour or entanglements. A small active
tension‑control motor (adding minimal complexity) might be needed to
damp oscillations.

5\. Human factors. Constant gentle tension from two points may feel
unfamiliar; the suit's attachment must not restrict blood flow or cause
discomfort over 6‑hour EVAs. Testing in neutral‑buoyancy pools will not
simulate the absence of gravity perfectly, so in‑orbit validation is
eventually required.

\-\--

7\. Integration with Original Atmospheric Project

This orbital concept shares the foundational philosophy of the original
Project Superman:

· Differential control via external force modulation (laser
intensity/angle instead of individual tube throttling).

· No moving nozzles, no gimbals.

· AI interpretation of body pose for thrust vectoring.

· Redundancy through distributed elements (two tethers, multiple
tracking patches).

It is, however, a radical departure from the energetic, chemical nature
of the solid‑fuel suit. The atmospheric version may still be developed
independently for its own niche. For vacuum EVA, this photonic tether
approach is unequivocally superior in safety, simplicity, and alignment
with the no‑waste philosophy.

\-\--

8\. Call to Action (Internal)

The core concept is now closed. What remains is the
hammer‑until‑it‑works engineering. Knox Makers' immediate next steps:

· Build a 1/4‑scale 3D‑printed mannequin with retroreflectors and a
simple two‑tether rig.

· Set up a small (5 W) laser pointer, webcam, and OpenCV pose‑tracking
script on a bench.

· Demonstrate closed‑loop "flight" along a line in a vacuum chamber.

· Then scale up.

This document is intentionally kept as a working design note, not a
formal public release. It captures the state of the art as of the date
above, for the collective's own use and for any future prior art
filings. All ideas herein are dedicated to the public domain; no patents
shall be filed.

"I just want to point my fist at the sky and not fall." -- E.M.

End of Addendum
