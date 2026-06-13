SUPER MOPED

A variable-geometry four-wheel sit-through electric moped with
hot-swappable modular components and a shared power/data docking
ecosystem.

Author: Eric Don McElroy

Date: 2026-06-08

Contact: eric.mcelroy@gmail.com, https://substack.com/@eskamick

Version: 1.0

Status: Public Release / Prior Art Disclosure

\-\--

Abstract

The Super Moped reimagines the urban two-wheeler as a dynamically
stable, four-wheeled platform that retains the narrow, sit-through
profile of a conventional moped. Its independent X-splay wheel geometry
continuously varies the track width from a door-friendly 30 inches to a
wide, planted stance at speed or when parked. Built around a common
hot-swap architecture first introduced in the Super Golf Cart, the
vehicle accepts slide‑in batteries, body panels, and accessories through
a proprietary keyed power‑and‑data docking interface. A single hardware
platform can be electronically governed to meet e‑bike, low‑speed
vehicle, or moped regulations, offering high torque with
software‑enforced speed caps. This disclosure places the full vehicle
system and its subcomponents into the public domain as prior art.

\-\--

Problem

Electrified micromobility is fragmented across regulatory classes
(e‑bike, moped, neighborhood EV) with little hardware commonality.
Riders who want a sit‑through, step‑through form factor are forced onto
two wheels, sacrificing stability at low speed and when stopped.
Existing four‑wheel solutions are either full‑width microcars or golf
carts---too wide to filter through traffic, pass through doorways, or
park on a sidewalk. None offer a single vehicle that can morph from
pedestrian‑friendly narrow mode to a stable high‑speed footprint, while
also letting owners swap batteries, bodywork, and motors without tools
and without buying an entirely new vehicle.

\-\--

Concept

The Super Moped is a four‑wheel, sit‑through electric vehicle that
physically occupies the same width envelope as a traditional moped
(\~30--32 in) in its most compact state. Four wheels are arranged in two
close‑coupled pairs---one pair under the rider's feet, one under the
seat. Each wheel is carried on an independent, extendable arm that moves
outward along an angled, non‑parallelogram path (the X‑splay geometry).
The arms are actuated by robust linear drives and can stop at any point
along their travel, giving the rider a continuously variable track
width.

Narrow mode (sidewalk, doorway, storage): wheels retracted to a 30 in
overall width, effectively forming two narrow tracks. Wide mode (speed,
cornering, parking): wheels extended outward in an X pattern, increasing
both front and rear track by several inches for a dramatically larger
stability footprint. The rider can manually select any width, or leave
the vehicle in automatic mode where speed and inertia sensors widen the
stance progressively. At a full stop, fully splayed wheels provide a
stable platform for mounting/dismounting.

Hot‑swap ecosystem. The chassis incorporates a standardized keyed
power‑and‑data bus (physical key‑shape mechanical docking port).
Batteries, motor controllers, body panels, and convenience modules
(radio, cup holder, lighting) mate to this bus using a common
slide‑and‑lock connector. Batteries are swappable in seconds without
tools; entire body sets can be changed by the owner---including
user‑fabricated panels (plywood, composites) that bolt to the dock's
mounting perimeter. The system is the same as that used in the Super
Golf Cart, enabling cross‑vehicle component sharing.

Drivetrain. Four off‑the‑shelf in‑wheel hub motors (one per wheel)
provide all‑wheel drive with independent torque vectoring. The motors
plug into the same docking standard, allowing future motor upgrades or
per‑wheel swaps in minutes.

Electronic class gating. The vehicle hardware is engineered for
moped‑class performance (up to \~45 km/h / 28 mph) but is electronically
limited to comply with lower classes (e.g., 20 mph e‑bike, 25 mph LSV)
through a simple software lock. The same physical unit can be sold into
multiple regulatory environments, with an upgrade path that keeps
components identical. Torque and acceleration remain high even when
speed is capped, giving responsive low‑end performance that surpasses
typical vehicles in the governed class.

\-\--

Feasibility

All core subsystems are assembled from commercially available,
production‑proven components.

· In‑wheel hub motors. Numerous manufacturers (QS Motor, Leafbike, Grin
Technologies) offer brushless hub motors in 500 W--3 kW continuous
ranges that fit within 10--14 in wheels. These are standard in
e‑scooters, e‑mopeds, and light electric ATVs.

· Controllers. Off‑the‑shelf FOC sine‑wave controllers (Kelly KLS,
VESC‑based designs) support CAN‑bus communication and torque‑vectoring
across multiple drive wheels.

· Battery packs. 48 V and 72 V lithium‑ion packs built from 21700
cylindrical cells with integrated BMS are used in volume by the electric
motorcycle industry (Zero, Sur‑Ron, HPC). Swappable pack housings can be
molded off‑the‑shelf.

· Variable‑geometry actuation. Heavy‑duty linear actuators (Thomson,
Linak) with integrated position feedback can move the wheel arms at
speeds sufficient for on‑the‑fly width changes. Similar actuation is
used in adjustable medical mobility bases and agricultural machinery.

· Docking connector. The keyed physical connector uses standard
amphenol‑style power contacts and a CAN‑bus data line; the keying is a
mechanical shell that ensures proper orientation and component‑family
matching. No novel electronics are required---only a custom molded
housing that can be prototyped via CNC and later injection‑molded.

· Vehicle dynamics. Analogous variable‑geometry concepts exist in the
Toyota i‑ROAD (active lean, three‑wheel) and the BMW Streetfighter
X‑track system (concept‑stage variable wheelbase). The Super Moped
replaces complex tilting linkages with a simpler independent radial
extension that maintains constant wheel alignment and steering geometry.

The narrow‑profile, all‑wheel‑drive architecture also benefits from
existing traction‑control algorithms used in electric wheelchairs and
mobile robots (ROS‑based packages). No fundamental invention is
required---only integration of known technologies.

\-\--

Challenges

· Mechanical rigidity of X‑splay arms. Each arm must resist braking,
cornering, and impact loads while maintaining accurate wheel alignment
across its full travel. Over‑constrained independent arms require
careful bearing selection and anti‑backlash design.

· Fail‑safe behavior. A loss of actuation power must not allow the
wheels to collapse. A mechanical locking mechanism (spring‑applied,
electrically released) or a self‑locking leadscrew can hold position.

· Software governance integrity. Electronically locking a vehicle that
is physically capable of higher speed demands robust tamper‑resistant
firmware; regulators may require hardware‑enforced limits in some
jurisdictions.

· Weight. Four independent suspension arms, four hub motors, and linear
actuators add mass compared to a conventional two‑wheel moped. Careful
material selection (aluminum arms, composite body panels) and the
ability to use a smaller battery in low‑speed configurations will
partially offset this.

· Certification fragmentation. Selling the same hardware into multiple
vehicle classes means navigating separate testing regimes (NHTSA, EU
type‑approval, etc.) even if the physical unit is identical.

\-\--

Development Path

1\. Prototype the variable‑geometry chassis. Build a static rolling
testbed with four independent X‑splay arms, manual actuation, and
unpowered wheels. Validate structural stiffness and width range.

2\. Integrate off‑the‑shelf hub motors and controllers. Verify low‑speed
stability in narrow mode and high‑speed behavior in wide mode. Tune
torque vectoring.

3\. Finalize the keyed docking standard. Iterate the physical connector
housing and pinout. Produce a small batch of battery and body‑panel
docks. Publish the mechanical specification as an open standard
alongside this disclosure.

4\. Software governance implementation. Develop an encrypted firmware
lock for speed class selection. Enable over‑the‑air updates for
reclassification and feature unlocks.

5\. Compliance test mule. Build a unit tuned to moped performance; carry
out simultaneous testing for e‑bike and LSV electronic limits. Document
all results for regulatory pre‑clearance.

6\. Platform extension. Use the same X‑splay chassis and docking bus for
a wheelchair variant, a cargo moped, and a lightweight enclosed cabin
microcar---all sharing the identical component ecosystem.

\-\--

Technology Stack

· Motors: QS 205 50H V3 hub motors (3 kW peak each) or equivalent, laced
to 12 in alloy rims.

· Controllers: Kelly KLS‑N sinusoidal controllers (one per wheel) or
VESC 100/250 for open‑source firmware.

· Battery: 72 V / 40 Ah lithium‑ion pack (LG M50LT 21700 cells), housed
in a slide‑in keyed dock with integrated BMS and CAN‑bus reporting.

· Data Bus: CAN 2.0B, with a proprietary keyed physical connector
carrying power, CAN‑H/CAN‑L, and a presence‑detect pin.

· Actuators: Linak LA36 12 V linear actuators (1500 N, 200 mm stroke)
with hall‑effect position feedback, one per wheel arm.

· Steering: Handlebar‑input with steer‑by‑wire to electronic rack
(custom, based on servo actuator) or direct linkage if wheel arm
geometry permits.

· Body: Modular bolt‑on composite or plywood panels; attachment points
built into the keyed dock housing's external frame.

· Vehicle Control Unit: Teensy 4.1 or STM32‑based VCU running
open‑source vehicle dynamics code, with OBD‑II/CAN diagnostics.

· Displays: 5 in sunlight‑readable TFT with CAN‑bus dashboard; Apple
CarPlay/Android Auto via wireless dongle optional.

\-\--

Author Note

This white paper is a public‑domain prior art disclosure, intended to
prevent patent encumbrance of the described system and to provide a
baseline reference for open‑source hardware developers. The Super Moped
platform, its X‑splay geometry, and the shared keyed docking bus are
placed into the public domain as of the publication date. Builders,
engineers, and companies are invited to study, replicate, and improve
upon the design without restriction. The author can be contacted at the
addresses above for technical clarification or collaboration.
