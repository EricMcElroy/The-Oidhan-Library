\# TECHNICAL SPECIFICATION: VOLUMETRIC SWEPT-VOLUME 3D DISPLAY
ARCHITECTURE

\### High-speed persistence-of-vision geometric display via a fluid
thermoformed helical matrix.

\*\*Author:\*\* Eric Don McElroy

\*\*Date:\*\* 2026-06-08

\*\*Contact:\*\* \[Eric.McElroy@gmail.com /
https://eskamick.substack.com/\]

\*\*Version:\*\* 1.0

\*\*Status:\*\* Public Release / Prior Art Disclosure

\## Abstract

This document outlines the architecture for an autostereoscopic,
swept-volume volumetric 3D display that leverages human persistence of
vision (POV) to render solid-looking physical geometry in mid-air. By
spinning a thermoformed thermoplastic helical ramp inside a sealed
optical atmospheric chamber at 1800 RPM and projecting coordinated
high-speed binary bit-planes up through the base, the system translates
temporal data streams directly into spatial 3D coordinates. The
implementation prioritizes structural baking over live computing loops
to achieve a zero-latency runtime pass-through.

\## 1. Core Architectural Breakdown

The system functions as a tightly coupled energy loop across three
distinct physical layers:

\### A. The Structural Matrix (Kinetic Layer)

\* \*\*The Containment Vessel:\*\* A heavy-walled (3mm to 4mm) cast
acrylic cylinder handles the structural load. The wall thickness is
scaled to eliminate asymmetric ovality deformation under high
centrifugal stress.

\* \*\*The Helical Diffuser:\*\* A single 360-degree Archimedean helix
thermoformed from a flat PMMA strip during its low-resistance thermal
fluid state (140\^\\circ\\text{C}). The surface is sandblasted
post-forming with fine aluminum oxide to create an anisotropic
semi-diffuse projection plane.

\* \*\*Atmospheric Seal:\*\* Aluminum pocket-cap end-plates seal both
ends of the tube. The trapped internal air reaches solid-body rotation
within seconds of spin-up, dropping continuous internal aerodynamic
resistance to zero.

\### B. The Carrier Wave Signal (Photonic Layer)

\* \*\*Bit-Plane Packing:\*\* To bypass standard operating system
frame-rate bottlenecks, the display data is pre-baked into a 150Hz
24-bit RGB video stream. Each frame acts as a carrier wave containing 24
independent, 1-bit binary spatial slices packed directly into the color
channels.

\* \*\*Hardware Demuxing:\*\* A high-speed FPGA controller decomposes
each incoming 24-bit frame into its constituent bit-planes, firing them
sequentially onto a Digital Micromirror Device (DMD) at a native
frequency of 3600Hz.

\### C. The Target Decoder (Human Gestalt Layer)

\* \*\*Passive Hardware Filtering:\*\* Rather than adding weight and
optical complexity via variable-focus lens groups, the system exploits
the shallow depth-of-field of the projector optics as a passive
anti-aliasing filter. The micro-blur between intersecting spatial planes
smoothly blends adjacent slices (N and N+1), matching the data density
to the low-pass integration window (30\\text{ms} - 50\\text{ms}) of the
human visual cortex.

\## 2. Off-The-Shelf (COTS) Technology Stack

The design intentionally utilizes high-volume, pre-baked hardware
ecosystems to minimize custom fabrication costs:

\| System Node \| Component Description \| Selected COTS Reference \|
Primary Core Function \|

\|\-\--\|\-\--\|\-\--\|\-\--\|

\| \*\*Projection Engine\*\* \| High-Speed DLP Development Kit \|
\*\*Texas Instruments DLPLCR4500EVM\*\* \| Delivers native 0.45\" WXGA
pattern streaming up to 4225Hz in 1-bit binary mode via dedicated
hardware trigger I/O. \|

\| \*\*Drive Motor\*\* \| Brushless Outrunner \| \*\*BrotherHobby 2808
(or T-Motor 2207 Stack)\*\* \| High-torque drone motor capable of
handling high radial loads and maintaining stable 1800 RPM (30 RPS)
under continuous load. \|

\| \*\*Speed Controller\*\* \| 32-Bit Brushless ESC \| \*\*Holybro
Tekko32 65A (BLHeli_32 Framework)\*\* \| Provides sensorless
commutation, active regenerative braking (Damped Light) to reclaim
spin-down energy, and native ERPM telemetry. \|

\| \*\*Sync Node\*\* \| 600MHz ARM Microcontroller \| \*\*Teensy 4.1
Development Board\*\* \| Captures real-time hardware interrupts from the
rotor shaft and drives the low-latency hardware trigger lines on the DLP
controller. \|

\| \*\*Position Sensor\*\* \| Incremental Optical Encoder \| \*\*Omron
E6B2-CWZ6C (1000 P/R)\*\* \| Tracks precise rotational angles (\\theta)
down to sub-degree increments, establishing the system\'s spatial master
clock. \|

\## 3. Identified Holes & Risk Vectors

While the core data and mechanical loops are theoretically sound,
transitioning this architecture to a physical desktop prototype exposes
three distinct implementation flaws that must be patched before
finalizing construction:

\### Hole A: The 2\\omega Optical Derotation Crisis

If a stationary projector fires up along the central axis of rotation
onto an internal mirror or prism that spins \*with\* the cylinder at
speed \\omega, the laws of reflection dictate that the bounced light
beam will sweep out into the room at exactly twice the mechanical speed
(2\\omega).

\* \*\*The Vulnerability:\*\* Because the helical screen is only
spinning at \\omega, the projected light beam will outrun the physical
display surface. This will completely tear the spatial geometry apart,
causing the image to smear into an unrecognizable ring of light.

\* \*\*The System Fix:\*\* Bypass the central axis mirror entirely.
Mount the DLP engine offset from the center line, firing directly
straight up through a clear ring on the bottom plate. The fixed vertical
beam will cross the spinning helix cleanly at a changing spatial height
(Z) relative to the motor angle (\\theta) without any rotational
multipliers.

\### Hole B: The Structural Adhesive Centrifugal Seam

The inner edge of the thermoformed helix must be bonded permanently to a
central stainless steel or carbon fiber axle.

\* \*\*The Vulnerability:\*\* At 1800 RPM, the joints experience a
continuous 180g peeling force pulling the plastic outward away from the
metal shaft. Standard cyanoacrylates or traditional epoxies are brittle
under cyclic vibration; they will crystallize and shear, causing the
helix to detach mid-spin and jam violently against the outer container
wall.

\* \*\*The System Fix:\*\* Implement an enterprise-grade structural
acrylic adhesive (e.g., \*\*Lord 200 or 3M Scotch-Weld DP8405NS\*\*).
These adhesives form a flexible, high-elongation polymer matrix that
chemically bites into the PMMA while maintaining high peel strength
against metal under heavy structural g-loads.

\### Hole C: The Mechanical Drive Hub Shear Point

The drive motor shaft must interface with the bottom aluminum pocket cap
to spin the high-mass assembly up to speed.

\* \*\*The Vulnerability:\*\* High angular acceleration during spin-up
puts immense torsional shear on the drive connection. If a basic
set-screw clamping flat on the motor shaft is used, it will slip or
score the metal, throwing off the rotary encoder timing and causing
unresolvable spatial jitter in the 3D output.

\* \*\*The System Fix:\*\* The bottom aluminum cap must be machined with
a native, tight-tolerance \*\*D-bore\*\* or a standard \*\*keyed
shaftway\*\* matching the motor output profile. Locking the torque
transfer into a physical geometric step completely removes the shear
load from the fastener, ensuring absolute clock synchronization between
the rotor and the encoder interface.
