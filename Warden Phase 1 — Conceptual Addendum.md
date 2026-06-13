Warden Phase 1 --- Conceptual Addendum

Evolved Subsystems: Power, Sight, Slack Management & Line Protection

Status: Living document, companion to the Phase 1 Prototype Blueprint

Date: 2026-06-10

Author: Eric Don McElroy (design evolution in collaboration)

Purpose: Capture the second-layer engineering concepts that emerged from
deep-diving the original Phase 1 architecture. These additions
significantly reduce battery dependence, eliminate the copper-wire
failure mode, improve aiming ergonomics, and add passive mechanical
safety fallbacks. They are presented as a conceptual addendum for future
bench integration once core launcher validation is complete.

\-\--

1\. Dual-Use Fuel System with Waste-Heat Harvesting

Problem: The original design required a separate high-discharge LiPo
battery for avionics, winch, and solenoid pulses, plus a propane/MAPP
canister for the launcher. Two consumables, two different refill cycles,
and battery sag risks under pulsed loads.

Solution: A single-fuel architecture where the propane/MAPP supply
generates both propulsive energy (combustion) and electrical energy
(solid-state waste-heat recovery). No engine, no alternator.

How it works:

· A small array of thermoelectric generator (TEG) modules is clamped to
the external surface of the steel breech block. After a shot, the breech
is hot (\~150°C), and the TEGs produce DC power via the Seebeck effect,
trickle-charging a supercapacitor bank.

· An optional micro pilot burner (soldering-iron catalyst head) taps the
same gas canister and provides a constant low-grade heat source for base
electrical power when the launcher is idle, ensuring continuous power
for avionics and sensors while stalking.

· Power hierarchy: TEGs → supercap bank → all transient loads (solenoid
kicks, winch pulses, camera, spark). A single 18650 Li-ion cell acts
solely as a cold-start seed and idle keep-alive. The battery is
virtually eliminated from cyclic operation.

· Fabrication: Off-the-shelf SP1848 TEGs, CPU heat sinks, CN3722 MPPT
charge controller, and a 6-cell series supercapacitor bank. Power path
managed by ideal diode ORing and a small custom PCB. Fully
makerspace-buildable.

\-\--

2\. Augmented Sighting System: Hip-Launcher Aiming

Problem: The launcher rides at pelvis height, well below the user\'s
natural line of sight. Targets are often high or at awkward angles. The
pilot needs to see exactly where the dart will go without contorting.

Solution: A bore-sighted micro FPV camera and laser designator feed a
wrist-mounted display, augmented by an IMU-based computed impact-point
reticle.

Components:

· Barrel-mounted camera: 1000TVL FPV board camera, zeroed to bore axis,
clamped to the barrel shroud. Transmits 5.8 GHz video to a small wrist
monitor or video watch.

· Laser designator: A visible red Class 3R laser module, also
bore-sighted, giving instant visual confirmation on the target.

· Gyro-stabilized reticle: A dedicated IMU on the launcher pivot tracks
barrel vector in 3D. The Teensy runs a simple ballistic drop model (from
bench velocity data) and overlays a computed impact point crosshair onto
the FPV feed via a MinimOSD chip.

· Operational loop: Twist hips to aim, glance at wrist display, place
reticle on target, fire. The reticle automatically compensates for angle
and drop.

Why it works with the power system: The camera, laser, and VTX together
draw about 5W continuous. The pilot-flame TEG can supply this
indefinitely. The OSD and IMU are negligible loads. No extra battery
hit.

\-\--

3\. Active Slack-Managed Launch Sequence (Copper Wire Protection)

Problem: The signal wire (24 AWG copper inside the Dyneema braid) is
essential for dart release. If it sees any axial tension---especially
during the load spike at dart impact or from Dyneema stretch---it will
snap.

Solution: A launch sequence that actively maintains slack in both the
Dyneema and copper lines throughout the entire flight and impact, then
separates their load paths so the copper never bears strain. This is
achieved through predictive spool-forward pay-out, a Dyneema-only clamp,
and a stretch-compensation reverse stroke.

Sequence details:

1\. Pre-ignition: The Dyneema spool is free and gives a small forward
pulse to create deliberate slack. The copper spool (spring-loaded, see
§4) also maintains its own slack.

2\. Ignition & dart acceleration: The Dyneema spool motor runs forward
in sync with the dart\'s expected acceleration profile (feedforward from
IMU launch detect and bench velocity data), paying out line at the same
rate the dart moves. The relative velocity between line and dart is near
zero, so the slack created in step 1 is preserved.

3\. Dart in flight: The line trails behind the dart, slack and
untensioned. The copper wire floats inside the Dyneema braid, also
slack. No axial load on either.

4\. Dart impact & fluke lock: The pelvic IMU detects the sharp
deceleration spike. The AI instantly triggers a mechanical clamp that
grips the Dyneema braid only (with a relief channel for the copper). The
Dyneema spool locks. The load begins to transfer.

5\. Stretch compensation: Immediately after the clamp engages, the
Dyneema spool rotates backward by a tiny calculated amount---just enough
to offset the 1--3% elastic stretch that occurs as the pilot\'s momentum
loads the line. This restores the copper\'s slack margin. The copper
itself was never clamped and never tensioned.

6\. Swing: The full load rides on the locked Dyneema. The copper is
slack inside the braid, protected.

Why this is superior: It eliminates the tension failure mode at the
source, rather than trying to cushion it after the fact. The copper is a
non-load-bearing passenger at all times.

\-\--

4\. Dual-Spool System: Dyneema (Powered) + Copper (Spring-Tensioned)

Problem: A single spool for both lines would force the copper to follow
every stretch and pay-out of the Dyneema, inevitably tensioning it. A
separate motorized spool for the copper adds complexity. But a fully
passive copper spool can tangle or back-lash without some tension
control.

Solution: Two independent spools on a common axis, with the Dyneema
spool actively driven and the copper spool fitted with a light
constant-force spring. The spring provides just enough gentle take-up to
keep the wire from birdnesting or flapping, but yields instantly to any
differential motion caused by Dyneema stretch or pay-out.

· Dyneema spool: Full motor control, large diameter, handles all
structural loads, executes the active slack and compensation strokes.

· Copper spool: Tiny, low-inertia, free-spinning with a coil spring
(like a retractable badge reel but smaller). It holds 24 AWG
silicone-insulated wire, terminating at the dart\'s solenoid pigtail.
The spring tension is under 0.1 N, negligible.

· Line coupling: The two lines are loosely joined along their length
with low-friction PTFE beads or a helical wrap that allows independent
sliding. This keeps the copper aerodynamic but not bonded.

Effect: The copper spool behaves like a self-tending fishing
reel---always wants to reel in gently, but any slight tug from the
Dyneema\'s motion pays it out instantly. No electronics, no motor, no
control logic needed for the copper. It\'s a perfect maker-solution: the
hard problem solved with a spring.

\-\--

5\. Mechanical Shock Buffer (Passive Fail-Safe)

Problem: The active slack management and Dyneema-only clamp handle the
load spike beautifully, but if the AI timing is off by even 20 ms or the
clamp solenoid fails, a sharp pull could still reach the pelvic frame
and the copper.

Solution: A dumb, passive mechanical buffer placed in the load path
between the winch and the nexus block, acting as a backup. If a sharp
spike gets past the active systems, the buffer absorbs it by converting
the energy into fluid shear or air compression, spreading it over time.

Two maker-friendly options:

· Rotary viscous slip clutch: A stacked-disc friction pack lubricated
with high-viscosity silicone oil, integrated into the winch spool axle.
Under sudden load, the discs slip against the oil\'s resistance,
allowing a fraction of a turn before a mechanical pawl locks them solid.
Heat dissipates the energy.

· Linear pneumatic dashpot: A small RC-car shock absorber placed in
series with the Dyneema line at the nexus block. Under a spike, the
piston compresses air through a small orifice, taking an inch or two of
stroke before bottoming out on a hard stop. Re-sets passively when
tension is released.

Integration: Both are tunable with fluid viscosity or orifice size and
require zero power or control. They sit in the load path and only act if
the active systems fail to mitigate the spike. This gives a graceful
degradation path.

\-\--

6\. Control Integration Notes

All the evolved subsystems map cleanly onto the existing Teensy 4.1
state machine and power architecture:

· State_Idle: Pilot-flame TEG powers base avionics, camera, and wrist
display. Supercap bank trickle-charged. Copper spool idle (spring holds
wire gently). Dyneema spool braked.

· State_Launch: On trigger, fuel injection pulse, spark, simultaneously
spool-forward motor profile to maintain slack. Camera and laser active.
All power from supercaps (transient).

· State_Flight/Impact: IMU detects impact, clamp solenoid fires, Dyneema
spool locks, then executes reverse compensation stroke. Copper spool
passively pays out any differential. Power pulse from supercaps,
immediately recharged by TEG array as breech heats.

· State_Swing: Low-power monitoring of line tension and IMU. Dyneema
locked. Copper slack and unloaded. TEG array recharging supercaps and
topping off battery.

· State_Release: 24V reverse pulse to dart solenoid via copper wire.
Winch retrieval. Copper spool rewinds spring tension as line shortens.

\-\--

7\. Fabrication Roadmap (Staged Integration)

All these additions are designed to be bench-tested and integrated
incrementally, only after the core launcher and fluke dart are proven:

1\. Bench validate launcher & dart (muzzle velocity, fluke lock in oak).

2\. Add TEG array to breech, characterize power output during cooldown.
Size supercap bank.

3\. Add FPV camera/laser/OSD to barrel shroud, test aiming accuracy from
hip.

4\. Build dual-spool assembly, test slack-maintenance launch sequence
with a stationary target.

5\. Test Dyneema-only clamp and compensation stroke under drop-gantry
loads. Verify copper wire survives 100 cycles.

6\. Install mechanical buffer as passive backup, confirm it doesn\'t
interfere with normal operation.

\-\--

This addendum is released as part of the Warden public prior art
disclosure. The concepts herein extend the original Phase 1 blueprint
and are offered without restriction for community development and
refinement. Attribution appreciated.

\-\--

This should serve as a clean, build-ready reference that captures the
full breadth of our design evolution. It\'s modular, so each section can
be pulled into the main white paper or worked on independently. Let me
know if you want any section expanded or a diagram sketched for the
spool arrangement or the power architecture.
