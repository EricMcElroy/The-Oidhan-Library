INKJET WALL PRINTER

A contact-based, dual-chain XY positioning system that prints
high-resolution images directly onto vertical surfaces using a
horizontally-oriented inkjet printhead, multi-pass smear-free routing,
and sensor-guided surface adaptation.

Author: Eric Don McElroy

Date: 2026-06-08

Contact: eric.mcelroy@gmail.com, https://substack.com/@eskamick

Version: 1.0

Status: Public Release / Prior Art Disclosure

\-\--

Abstract

The Inkjet Wall Printer is a vertical-surface printing system that
mounts a reoriented inkjet printhead onto a dual-chain XY carriage
positioned flat against a wall. The system employs a multi-pass,
spaced-stripe printing strategy that keeps guide wheels on dry surface,
eliminating ink smear. Proprietary wall primer enables compatibility
with off-the-shelf aqueous pigment inks. Onboard cameras and sensors
track printed reference dots for continuous registration and adapt to
surface irregularities such as brick or textured render. The platform
scales from indoor fine-art murals to building-façade printing using
airbrush nozzles and scaffold-mounted rails. This disclosure places the
contact wall-printing architecture and its smear-free multi-pass method
into the public domain.

\-\--

Problem

Vertical-surface printing remains dominated by manual
methods---hand-painting, stenciling, or vinyl application---or by
expensive industrial flatbed printers that cannot handle large,
irregular, or already-installed walls. Existing automated wall printers
are rare, often require perfectly smooth surfaces, and struggle with ink
drying time, causing wheels or guides to smear wet ink. No open standard
exists for a modular, scalable contact wall printer that can adapt to
common architectural surfaces and accept user-supplied materials.

\-\--

Concept

The Inkjet Wall Printer is a dual-chain, XY-positioned contact printer
designed to hang flat against any vertical surface. The frame is
temporarily anchored to the wall (suction cups, removable anchors, or a
floor-standing tension rig) and positions a carriage holding a
horizontally-oriented inkjet printhead.

Printhead and Ink System

An off-the-shelf industrial piezo printhead (e.g., Xaar 128 or Epson
DX‑series) is rotated 90° so that the nozzle face is parallel to the
wall, firing ink horizontally at a throw distance of \~1 mm. The ink
system uses standard aqueous pigment inks, chosen for cost and wide
availability.

Paint compatibility. The wall must be pre-coated with a proprietary
primer---a silica‑loaded acrylic water‑based coating that creates a
micro‑porous, inkjet‑receptive surface identical in function to the
coating on inkjet photo paper. The primer is applied by roller or spray
before printing and dries to a matte white finish. Any standard aqueous
pigment ink then bonds instantly with high color density and zero bleed.
This approach requires no custom ink formulation, no UV curing hardware,
and no solvent handling, while delivering photo‑quality results on any
substrate---brick, render, drywall, or wood.

Multi-Pass Smear-Free Printing

The carriage is guided by soft, non‑marring wheels that ride directly on
the wall. To prevent the wheels from rolling over wet ink, the printer
uses a multi-pass, spaced-stripe strategy:

1\. Pass 1: The carriage prints a series of vertical stripes separated
by dry gaps wider than the wheel contact patch.

2\. Pass 2: The carriage indexes horizontally and prints a second set of
stripes, again leaving gaps.

3\. Final pass: All remaining gaps are filled, at which point the
previously printed stripes are fully dry. The wheels always track on a
dry, printed or unprinted surface.

Printing is bidirectional (both carriage travel directions) to maximize
throughput.

Registration and Surface Adaptation

Upon startup, the printer lays down a series of small guide dots at
known positions. One or more global‑shutter cameras on offset arms
continuously observe these dots. If the carriage shifts relative to the
wall (due to vibration, chain slack, or surface irregularity), the
system computes the offset and adjusts printhead firing in real time.
Multiple cameras ensure at least one reference dot remains in view
regardless of carriage position, eliminating occlusion dead zones.

For irregular surfaces such as brick or textured render, the carriage
periodically pauses. A laser time‑of‑flight rangefinder or a small
structured‑light depth sensor maps the local surface contour. The
printhead height is adjusted dynamically, and ink droplets are fired
selectively to avoid deep mortar joints or protrusions. The result is a
clean image even across non‑planar walls.

Positioning System

The carriage is suspended by two motor‑driven chains (or toothed belts)
that provide X and Y positioning, identical in principle to a vertical
pen plotter. Stepper motors with closed‑loop encoders drive the
sprockets, maintaining sub‑millimeter positioning accuracy. The entire
frame is lightweight and can be assembled by two people.

Scaling to Building Size

For large‑scale façades, the fine inkjet printhead is replaced with an
array of airbrush nozzles or large‑orifice spray heads fed by standard
exterior acrylic latex paint. The same XY positioning logic applies, but
the carriage rides on scaffold‑mounted rails. A safety guide bar on the
far side of the carriage prevents wind from pushing it off the wall. DPI
drops to 2--10, appropriate for mural viewing at distance. The core
smear‑free multi‑pass strategy and vision registration remain identical.

\-\--

Feasibility

All components are commercially available and have been demonstrated in
analogous systems.

· XY positioning. Dual‑chain vertical plotters are a mature technology
in large‑format vinyl cutters and CNC routers (e.g., Makermade, Maslow).
Scaling a dual‑motor chain drive to wall dimensions uses identical
kinematics.

· Printhead. Industrial piezo printheads (Xaar, Konica Minolta, Epson)
are designed for flatbed printers and can be mounted in any orientation.
Driver boards (e.g., Inktec JetDriver) are available off‑the‑shelf.

· Primer formulation. Silica‑alumina coatings for inkjet receptivity are
well‑known (Cabot CAB‑O‑SIL, Evonik AEROSIL); the primer is a
straightforward acrylic‑latex base mixed with these fillers, producible
by any paint manufacturer.

· Vision registration. OpenMV or Raspberry Pi global‑shutter cameras
with AprilTag or simple dot‑tracking algorithms provide sub‑pixel offset
measurement. Multi‑camera fusion is standard in robotics.

· Surface sensing. VL53L1X time‑of‑flight sensors cost under \$5 and
provide millimeter‑accurate distance readings at up to 4 m range. A
small array of these on the carriage maps surface relief in real time.

· Analogous systems. The WallPen and Vertical Printer Co. offer
commercial wall printers, but they use expensive UV inks and do not
employ the multi‑pass dry‑gap strategy or an open primer standard. The
disclosed system's novelty lies in its smear‑free routing, open‑material
philosophy, and surface‑adaptive sensing.

\-\--

Challenges

· Drying time management. The multi‑pass strategy assumes ink dries
between passes. In high humidity or on low‑porosity primer, this may
require a small warm‑air blower on the carriage, adding weight and
complexity.

· Primer application. Requiring a pre‑coat step may deter some users.
The primer must be demonstrably cheaper and easier than UV‑curable ink
alternatives.

· Chain vibration. Long‑span chain drives can oscillate, causing
positional error. Tensioners and damped guide rails are required.

· Bidirectional color alignment. Printing in both directions with a
multi‑color printhead requires precise timing to avoid color plane
misalignment between forward and reverse passes.

· Outdoor durability. Aqueous pigment inks are not inherently
waterproof. A post‑print clear coat or a weatherproof primer‑embedded
sealer may be needed for exterior murals.

\-\--

Development Path

1\. Benchtop XY carriage. Assemble a 1 m × 1 m chain‑driven testbed with
a dummy printhead and validate positioning accuracy and vibration
characteristics.

2\. Multi‑pass print algorithm. Implement the spaced‑stripe logic on the
testbed using water on a whiteboard to simulate ink; verify wheels
remain dry across all passes.

3\. Primer formulation. Partner with a coatings manufacturer to produce
a silica‑acrylic wall primer. Test with standard Epson Duraglow pigment
inks for dot gain, drying time, and adhesion.

4\. Vision registration. Integrate a global‑shutter camera and guide‑dot
tracking; demonstrate real‑time offset correction during a print.

5\. Surface adaptation module. Mount a VL53L1X array and code the
height‑compensation routine. Test on brick, pebbledash, and corrugated
metal.

6\. Full‑scale wall prototype. Build a 3 m × 3 m frame and print a
photographic mural on primed drywall. Collect data on print time, ink
consumption, and registration accuracy.

7\. Building‑scale variant. Develop the airbrush‑head module and
scaffold rail system. Conduct an exterior mural pilot project.

8\. Open‑source release. Publish the XY frame CAD, printhead mount,
primer formula, and control firmware under a permissive license.

\-\--

Technology Stack

· Printhead: Xaar 128 (piezo drop‑on‑demand, 200 DPI native) or Epson
DTG printhead; 4‑color CMYK plus optional white.

· Ink: Aqueous pigment ink (Nazdar or Dupont Artistri), 500 mL
cartridges.

· Primer: Water‑based acrylic‑latex with 15 wt% fumed silica and 5 wt%
alumina trihydrate; applied by 10 mm nap roller.

· Positioning motors: NEMA 23 closed‑loop steppers (2.5 N·m), driven by
Trinamic TMC5160 controllers with magnetic encoders.

· Chains: ANSI #25 roller chain with tensioner idler sprockets; aluminum
frame extrusion (80/20 40‑series).

· Carriage wheels: 40 mm polyurethane soft‑tread rollers (Shore A60),
offset from printhead by 100 mm.

· Vision cameras: 2× OpenMV Cam H7 Plus (global shutter, Aptina MT9V034
sensor) with 120° wide‑angle lens.

· Surface sensors: 5× VL53L1X time‑of‑flight laser rangefinders,
arranged in a cross pattern on the carriage face.

· Carriage compute: Raspberry Pi 4 running custom Python/C++ software;
path planning via GRBL‑HAL with wall‑printer kinematics fork.

· Dry‑assist: Optional 50 W PTC warm‑air blower with 3‑speed fan for
high‑humidity environments.

· Power: 24 V DC power supply (mains); optional battery operation with
KIB‑compatible 6S lithium pack for remote locations.

\-\--

Author Note

This white paper is a public‑domain prior art disclosure. The described
contact wall‑printing architecture---including the dual‑chain XY
positioning, horizontally‑oriented inkjet printhead, multi‑pass
smear‑free stripe strategy, vision‑based registration, surface‑adaptive
sensing, and silica‑acrylic primer standard---is placed into the public
domain for unrestricted use by builders, artists, and manufacturers. The
intention is to establish an open, low‑cost alternative to proprietary
wall printers and to foster community‑driven development. For technical
collaboration, contact the author at the addresses above.
