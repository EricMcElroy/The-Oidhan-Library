\# CAGE: Crowd Aerial Gentle Extraction System

\### Technical Concept White Paper

\*\*Author:\*\* Eric Don McElroy

\*\*Date:\*\* 2026-06-05

\*\*Contact:\*\* \[public disclosure -- no direct contact\]

\*\*Version:\*\* 1.0

\*\*Status:\*\* Public Release / Prior Art Disclosure

\-\--

\## Abstract

A slow, padded, overhead‑deployed capture cage that extracts individuals
from a crowd without impact, projectiles, or falls. The system relies on
psychological deterrence (visible, inescapable capture) and redundant
physical safety layers (pressure sensors, force limits,
human‑in‑the‑loop) to make non‑lethal crowd control safer than any
existing tool -- from bean bags to water cannons. The core insight is
that crowds fear \*certain capture\* more than pain, and a few
extractions are enough to disperse a protest without injury.

\-\--

\## Problem Statement

Current less‑lethal crowd control tools (bean bags, rubber bullets,
water cannons, tear gas, tasers) all share the same flaws: they rely on
impact or irritation, they frequently cause serious injury or death, and
they give a crowd no clear signal of "this is over for you." Officers
must aim, judge force, and risk user error. A person can run, hide, or
fight through pain. No existing system offers \*certain, low‑trauma
removal\* of a single individual from a dense crowd.

What is missing is a tool that:

\- Inflicts no blunt or penetrating trauma.

\- Eliminates falls as a primary injury mechanism.

\- Removes officer aiming and force judgment.

\- Acts as a visible, predictable deterrent.

\- Works in open areas where crowds gather (plazas, streets, fields).

\-\--

\## Concept Overview

The system consists of a truck‑mounted hydraulic crane boom (or large
UAV) carrying a 360° padded cage. The cage is roughly 24" wide × 18"
deep × 84" tall -- just larger than a human body. It has a non‑slip
floor and padded interior walls. The cage is normally open at the
bottom. Deployment sequence:

1\. \*\*Vehicle positions\*\* at the edge of a crowd with clear overhead
clearance and an identified escape route for the crowd.

2\. \*\*Operator\*\* uses cameras and AI to select a target individual.
The cage is lowered slowly (walking pace) toward that person.

3\. \*\*Push rods\*\* (force‑limited paddles) extend from the cage
bottom to gently clear bystanders, creating a bubble around the target.

4\. \*\*Cage descends\*\* over the target. Pressure sensors on all
closing edges stop movement at ≤50 lbs of resistance.

5\. \*\*Ankle bar\*\* (optional) closes below knee height to prevent
stepping out -- no foot‑scoop that would cause a fall.

6\. \*\*Cage lifts\*\* the person a few inches off the ground. Interior
clearance allows at most a 12" drop; padded walls prevent injury from
leaning or falling.

7\. \*\*Crane retracts\*\* and moves the captured person to a secure
area for release or arrest.

If full closure is impossible (person hanging on exterior, crowd too
dense), the cage stops and retracts to 3 feet above ground, then drags
backward as a padded wall to create space.

\-\--

\## Why This Works --- Feasibility Basis

\- \*\*Physics:\*\* Low speed (\<0.5 m/s) and large padded contact area
produce negligible impulse and pressure. Injury forces are avoided by
staying below known thresholds for soft tissue damage (\<\< 100 lbs over
100 cm²). The 12‑inch maximum fall inside the cage is comparable to a
step off a low curb -- not a fall from standing height.

\- \*\*Engineering:\*\* Hydraulic cranes, boom lifts, and padded
restraint systems are mature, off‑the‑shelf technologies. Pressure
sensors, light curtains, and force‑limiting actuators are standard in
industrial robotics. AI object detection (person identification) is well
beyond what is needed for a human‑confirmed system.

\- \*\*Safety redundancy:\*\* Three independent sensor modalities
(capacitive, resistive, optical) vote on closure. A mechanical fuse
(collapsing link) backs up electronics. Human operator must confirm each
capture.

\- \*\*Psychological:\*\* Crowd dispersal via fear of capture is well
documented in animal behavior and human riot dynamics. Visible, slow,
unstoppable capture changes cost‑benefit calculations faster than
pain‑based tools.

No law of physics, nor known engineering limit, prevents this system
from working as described.

\-\--

\## Known Engineering Challenges

\| Challenge \| Mitigation Status \|

\|\-\-\-\-\-\-\-\-\-\--\|\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--\|

\| Overhead clearance (trees, wires, indoors) \| Operational constraint
-- system not used there \|

\| Crowd density preventing bubble clearance \| Push rods with force
limits; if fails, abort \|

\| Person climbs or jumps out during closure \| Top mesh + ankle bar +
closure speed \> reaction \|

\| Bystander wanders in at last second \| Light curtain + audible
warning + manual abort \|

\| Power loss during lift \| Mechanical brake (fails locked) + backup
battery \|

\| Hydraulic line rupture \| Dual actuators + check valves + spring
return to open \|

\| AI misidentification \| Human confirmation + two different AI models
\|

\| Person grabs exterior during lift \| External capacitive sensors stop
lift \|

\| Crane tip‑over \| Outriggers + gyroscopic tilt sensor + load cell
cutoff \|

\| Crush if sensor fails \| Three redundant sensors + mechanical fuse \|

All challenges have known engineering solutions or operational rules.
None are showstoppers.

\-\--

\## Suggested Development Path

1\. \*\*Prototype 0:\*\* Manual boom lift (existing bucket truck) +
padded plywood cage with hand‑operated closure. Test on volunteers with
no lift -- just enclosure. Validate interior clearances and fall safety.

2\. \*\*Prototype 1:\*\* Add hydraulic closure with pressure sensors and
a simple AI camera (e.g., OpenCV person detection). Test on stationary
dummies, then consenting adults. Measure closure forces and fall
distances.

3\. \*\*Prototype 2:\*\* Mount on small truck with outriggers. Integrate
push rods and light curtain. Test in simulated crowd (moving mannequins
on wheels).

4\. \*\*Field trial:\*\* Live demonstration with law enforcement
oversight, no actual arrests -- only volunteer "targets" who consent.
Refine human‑in‑the‑loop UI.

5\. \*\*Certification:\*\* Pass industrial robot safety standards (ISO
10218) and crowd control use‑of‑force guidelines.

Total estimated time: 18‑24 months for a deployable prototype. Cost:
\<\$500k for development (leveraging existing crane and robotics
components).

\-\--

\## Why Now

Three trends make this concept viable today:

\- \*\*Affordable hydraulic boom lifts\*\* (rental fleet) and electric
UAVs capable of lifting 400 lbs (emerging heavy‑lift drones).

\- \*\*Low‑cost pressure sensors and light curtains\*\* (industrial
safety equipment is commoditized).

\- \*\*Public demand for less lethal alternatives\*\* after documented
deaths from rubber bullets, bean bags, and tasers. The political window
for novel, visibly safer tools is open.

\- \*\*AI person detection\*\* (YOLO, Detectron2) runs on cheap GPUs and
can be verified by human operators.

What was missing 10 years ago (cheap computing, cheap sensors, public
acceptance of drones) now exists.

\-\--

\## Appendix: Available Technology & Prior Art

\| Item \| Description \| Source / Availability \|

\|\-\-\-\-\--\|\-\-\-\-\-\-\-\-\-\-\-\--\|\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--\|

\| Hydraulic boom lift \| Truck‑mounted, 40‑ft reach, 500 lb lift
capacity \| Genie, JLG (rental or purchase) \|

\| Pressure sensors \| Resistive or capacitive force sensing for closure
edges \| Tekscan, FSR, industrial automation suppliers \|

\| Light curtain \| Infrared safety curtain to detect intrusions \|
Banner, SICK, Keyence \|

\| Mechanical fuse \| Collapsing link with set failure load \|
McMaster‑Carr, custom spring‑loaded pins \|

\| AI person detection \| YOLOv8, Detectron2, or custom CNN \| Open
source (PyTorch, TensorFlow) \|

\| Push rod actuators \| Electric linear actuators with force feedback
\| Firgelli, Thomson, Progressive Automations \|

\| Non‑slip flooring \| Industrial anti‑slip matting (padded) \|
Grainger, McMaster‑Carr \|

\| Polycarbonate panels \| Transparent, impact‑resistant for cage walls
\| Lexan, Plexiglas (local plastics supplier) \|

\*\*Additional references:\*\*

\- ISO 10218: Robots and robotic devices -- Safety requirements.

\- National Institute of Justice (NIJ) standards for less‑lethal
projectiles (for contrast -- this system does not use projectiles).

\- "Rescue hook" extraction devices used by fire departments (mechanical
under‑arm lift).

\- Industrial robot force‑limiting standards (ISO/TS 15066).

\-\--

\## Author Note

I spent a decade inside a prison, got shot with less‑lethal munitions,
and watched officers struggle with tools that hurt people more than
necessary. This design started as an air cannon, then a push pole, then
a crane‑mounted cage. The pivot to "capture instead of strike" came from
watching how crowds react to certainty. I am releasing this as public
prior art so no one can patent it. Build it, improve it, and please --
test it on volunteers before it ever meets a crowd.

\-\--

\*This document is released as a public prior art disclosure. The author
asserts origination of the concept as described herein as of the date
above. No patent is claimed. Builders are free to develop, implement,
and commercialize this concept without restriction or licensing
requirement. Attribution appreciated but not required.\*

\*© Eric Don McElroy --- Released to the public domain.\*
