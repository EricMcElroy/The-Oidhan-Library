AI WELDING GOGGLES

A peripheral augmented-reality welding mask that preserves a direct
optical view of the arc while overlaying 3D wireframes, enhanced
workspace pass‑through, and contextual data in the surrounding field of
vision.

Author: Eric Don McElroy

Date: 2026-06-08

Contact: eric.mcelroy@gmail.com, https://substack.com/@eskamick

Version: 1.0

Status: Public Release / Prior Art Disclosure

\-\--

Abstract

The AI Welding Goggles invert the standard augmented-reality paradigm by
retaining a physical, auto-darkening central window through which the
welder directly views the arc and weld puddle. AR functionality is
confined entirely to the peripheral field---surrounding the window with
AI‑generated 3D wireframes, HDR pass‑through video of the workspace, and
contextual data---so the welder's primary visual channel is never
mediated by a camera. Integrated inside‑out tracking locks a CAD‑based
wireframe to the workpiece in real time. A hot‑swappable battery and
optional belt‑worn compute module connect via the Keyed Interlock Bus
(KIB) standard. This disclosure places the peripheral‑AR welding mask
architecture into the public domain.

\-\--

Problem

Conventional welding masks force a trade‑off: a passive shade protects
the eyes but blinds the welder to everything outside the arc, while
camera‑based "pass‑through" systems replace direct sight with a screen,
introducing latency, resolution loss, and a fundamental distrust among
professional welders who demand an optical view of the puddle. Existing
AR welding concepts attempt full‑field digital overlay, but overlaying
graphics atop an already‑darkened arc view washes out the puddle or
reduces contrast. A solution that preserves the direct optical path for
the critical welding zone while adding unobtrusive augmentation to the
surrounding workspace has not been productised.

\-\--

Concept

The AI Welding Goggles are built on a standard auto‑darkening welding
mask shell. The innovation is optical: the central 50--60 mm of the lens
area is a conventional passive/ADF filter stack, providing a clear,
undigitised view of the arc at shade levels 9--13. Surrounding this
window, the remaining interior surface is coated with a see‑through AR
waveguide or a reflective free‑space combiner that receives an image
from an embedded micro‑OLED projector. This peripheral display wraps the
direct view with:

· 3D wireframe overlay. A real‑time, AI‑registered wireframe of the
workpiece, derived from a pre‑loaded CAD file or a rapid stereo‑depth
scan taken before the arc is struck. The wireframe appears locked to the
physical part, visible even through the darkened lens, giving the welder
an "X‑ray" sense of the joint and final geometry.

· HDR workspace pass‑through. External global‑shutter cameras capture
the surrounding room at high dynamic range. The feed is
luminance‑flattened and composited onto the peripheral display,
effectively "lighting up" the dark workshop while the arc remains
contained in the central window.

· Contextual data. Welding parameters (amperage, voltage, travel speed,
gas flow) are displayed at the edges, fed via Bluetooth or KIB from the
welding machine.

The mask does not obstruct the welder's direct sightline. The AR
operates purely in the surrounding zone, augmenting situational
awareness without interfering with the critical central task.

Tracking and AI. Stereo global‑shutter cameras and an IMU perform
inside‑out SLAM to track the welder's head pose and anchor the wireframe
to the workpiece with sub‑millimetre accuracy. Fiducial stickers on the
workpiece or jig can optionally improve registration. The AI runs on an
embedded module (NVIDIA Jetson Orin Nano or Qualcomm Snapdragon SOM)
that consumes approximately 7--15 W, housed either in the mask shell or
an external belt pack.

Power and KIB integration. A hot‑swappable lithium‑polymer battery
(50--100 Wh) docks into the rear strap via a micro KIB port, identical
to those in the Keyed Interlock Bus ecosystem. An optional belt‑worn
compute module connects to the mask through a second KIB port,
offloading processing for heavier tasks and reducing head‑mounted mass.

\-\--

Feasibility

All core technologies are commercially available and can be integrated
without fundamental invention.

· Peripheral AR optical stack. Birdbath or waveguide combiners that
project into the periphery while leaving a central clear aperture are
produced by companies such as Lumus and Optinvent. These are used in
monocular enterprise headsets and can be adapted to a welding mask form
factor by replacing the central waveguide zone with a transparent ADF
cartridge.

· Auto‑darkening filter. Standard ADF cartridges (e.g., from 3M
Speedglas, Lincoln Viking) provide the central window and can be trimmed
or masked into the AR optic. Their switching speed (\<0.1 ms) and
optical clarity are proven.

· HDR cameras and pass‑through. Sony IMX678 global‑shutter sensors
provide 120 dB HDR and are used in automotive and machine‑vision
applications. Real‑time tone‑mapping can flatten the arc brightness for
peripheral display without affecting the direct view.

· AI tracking and wireframe rendering. Monocular and stereo SLAM are
mature in robotics (ORB‑SLAM3). CAD registration is achieved using
point‑cloud matching (ICP) with a pre‑scanned mesh. The wireframe
rendering is lightweight and can run on an embedded Jetson module at
60 fps.

· KIB battery and compute module. The micro KIB connector is identical
to that specified in the Keyed Interlock Bus white paper, providing
power, ground, and I²C data. The battery is a standard 4S1P
lithium‑polymer pack (14.8 V, 5000 mAh) with an integrated BMS,
hot‑swappable during a pause in work.

· Analogous systems. The Lincoln Electric VRTEX welding simulator uses
AR for training, and the Seer Lens wearable camera system provides
pass‑through welding recording. No current product combines peripheral
AR with direct optical arc viewing in a production welding mask.

\-\--

Challenges

· Optical alignment. The AR waveguide and the central ADF must be
seamlessly blended to avoid a visible border or double image at the
transition zone. This requires precision moulding and optical bonding.

· Weight and balance. Adding cameras, a projector, electronics, and a
battery to a welding mask increases mass, potentially causing neck
strain over long shifts. The belt‑worn compute option mitigates this.

· Latency in pass‑through. The peripheral pass‑through must be
synchronised with the welder's head motion. Any perceptible lag between
the direct arc view and the surrounding video can induce disorientation.
Target latency is ≤20 ms end‑to‑end.

· Arc interference. High‑frequency TIG arc starting and MIG spray
transfer can produce electromagnetic noise that may disrupt cameras and
processors. Shielding, ferrite chokes, and filtered power rails are
essential.

· Cost. Early prototypes using discrete AR optics and high‑end
processors will be expensive; the path to a consumer price point
requires custom waveguide fabrication at volume.

\-\--

Development Path

1\. Bench‑top optical prototype. Modify a standard welding mask by
inserting an ADF cartridge into a waveguide combiner blank. Validate
that the peripheral display is visible against the darkened central
zone.

2\. Camera and SLAM integration. Mount stereo cameras on the mask front,
run ORB‑SLAM3 on an off‑board laptop, and test wireframe registration
against a known workpiece.

3\. Pass‑through compositing pipeline. Develop real‑time HDR
tone‑mapping that blends the exterior camera feed into the peripheral
display without washing out the wireframe.

4\. KIB battery dock integration. Install a micro KIB port on the rear
strap, fabricate a compatible battery module, and test hot‑swap during
simulated welding sessions.

5\. Professional welder trials. Place prototypes with certified welders,
collect feedback on wireframe accuracy, peripheral visibility, comfort,
and trust in the direct‑view window.

6\. Cost‑reduction and open‑source release. Publish the optical stack
CAD, KIB connector pinout, and SLAM configuration as open‑source
reference, targeting a sub‑\$1,000 bill of materials at scale.

\-\--

Technology Stack

· Optics: Lumus OE‑33 waveguide combiner with central rectangular
cutout; 3M Speedglas 9100 ADF cartridge bonded into the aperture.

· Micro‑display: Sony ECX336A OLED (0.5‑inch, 1920×1080, 2000 nits) with
collimating lens.

· Cameras: 2× Sony IMX678 global‑shutter sensors with 185° fisheye
lenses for SLAM and HDR pass‑through.

· Compute (on‑board): NVIDIA Jetson Orin Nano (8 GB RAM) running ROS 2
and ORB‑SLAM3 at 60 fps.

· Compute (belt‑worn): Optional Jetson Orin NX module in a KIB‑tethered
belt pack with additional battery capacity.

· Tracking: Bosch BMI270 IMU, stereo SLAM with fiducial marker fallback
using AprilTags.

· Power: 4S1P Li‑Poly pack (14.8 V, 5000 mAh, \~74 Wh), hot‑swappable
via micro KIB port; voltage regulated to 5 V/12 V rails.

· Connectivity: CAN bus (ISO 11898‑2) for welding machine data; I²C for
KIB module ID; Bluetooth 5.3 LE for parameter display.

· Software: Custom Unity or Unreal Engine 5 rendering front‑end for
wireframe and HUD; point‑cloud registration using Open3D.

\-\--

Author Note

This white paper is a public‑domain prior art disclosure. The peripheral
augmented‑reality welding mask architecture---specifically the
combination of a central direct‑view auto‑darkening window surrounded by
an AR overlay fed by AI‑tracked wireframes and HDR pass‑through---is
placed into the public domain for unrestricted use by builders,
manufacturers, and open‑source hardware developers. The KIB power and
compute interconnects are detailed in the Keyed Interlock Bus white
paper, also in the public domain. For technical discussion or
collaboration, contact the author at the addresses above.
