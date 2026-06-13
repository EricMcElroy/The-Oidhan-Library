Addendum to Project Superman White Paper

Date: 2026-06-12

Authors: Eric McElroy & Knox Makers Collective

Status: Revision 1 -- Closing the Gaps

This addendum captures refinements made during a deep critique session.
The original white paper stands, but the following clarifications and
simplifications remove unnecessary complexity and align the project with
practical, fast‑iteration testing.

\-\--

1\. Name Confirmed

SUPERMAN'S VOLITION (no change)

\-\--

2\. Major Simplifications (Based on Critique)

2.1 No Thermoelectric Generators (TEGs) / Heat Recovery

· Original: Wrap nozzles with TEGs to recover waste heat for
electronics.

· Revision: Omitted. Weight and complexity outweigh marginal gain. The
engine cycle itself is efficient enough. Electronics will run on a small
battery (recharged on ground). Hot nozzles are fine -- we'll manage
pilot shielding with ceramic insulation.

2.2 No Wind Tunnel Required

· Original: Need laminar flow, hot‑wire anemometer.

· Revision: A leaf blower or even a box fan with a crude duct is enough.
We only need relative change in thrust with airspeed, not absolute
calibration. "Shaky is fine."

2.3 No Catapult / Ground Launch Rig

· Original: Catapult or JATO to reach takeover speed.

· Revision: The engine array can be sequenced to provide slow,
controlled lift from standing start. Fire a few tubes at low throttle,
use their waste heat to preheat adjacent tubes, then fire more. This
becomes a control problem, not a physics problem. Vertical takeoff
without stored energy is plausible.

2.4 No Fancy Air Metering for Intake Testing

· Original: Pitot tube, mass flow sensor.

· Revision: Simple pressure tap and a manometer. Math fills the rest.

2.5 Parachute Placement Not Critical

· Original: Back‑mounted only.

· Revision: Front, side, ankle‑mounted -- any location works. We'll test
and choose later.

2.6 Emergency Fuel Cutoff Does Not Need Purge

· Original: Nitrogen purge to clear residual acetylene.

· Revision: Residual gas burns out in \<1 second. Harmless. Cut screw
feeders; the remaining acetylene self‑consumes.

\-\--

3\. Revised Testing Stages (Lean & Mean)

Stage 0 -- Control & AI Validation (No Engine)

· Rig: Strings, pulleys, small weights or electric fans on a mock frame.
Use the same camera/IMU/software stack.

· Goal: Prove that differential thrust vectoring works, AI maps fist
direction to attitude, and failsafe logic triggers correctly.

· Cost: Scrap wood, cheap fans, Arduino -- under \$200.

Stage 1 -- Cold Flow (Tesla Valve Only)

· Rig: Single tube with Tesla intake, no ignition. Connect to shop air
or leaf blower.

· Measure: Pressure drop forward vs. reverse. Confirm diode effect.

· Pass criterion: Reverse leakage \< 20% of forward flow at same delta
P.

Stage 2 -- Micro‑Scale Hot Fire (Deflagration Mode)

· Tube diameter: 1--2 cm (may not detonate; deflagration is fine for
scaling data).

· Fuel: Grams of calcium carbide, syringe pump for water.

· Measure: Thrust, fuel consumption, tube temp, pulse frequency.

· Goal: Establish scaling laws for thrust vs. diameter, length, mixture.

Stage 3 -- Scale‑Up Tube (Detonation Mode)

· Diameter: 3--5 cm (above cell size for acetylene‑air).

· Same measurements as Stage 2. Compare to scaled predictions.

· Pass criterion: Thrust per cross‑section ≥ 2 N/cm² at reasonable fuel
flow.

Stage 4 -- Small Array (4 Tubes) on Test Stand

· Mount: Backplate with independent screw feeders.

· Test: Differential fueling for yaw/pitch. Measure crosstalk between
tubes.

· Pass criterion: Vector authority (moment) ≥ 20% of maximum thrust.

Stage 5 -- Tethered Human (Rotating Boom)

· Rig: Central pivot allows full angular freedom but limits altitude.

· Pilot: Wears full suit, engines running. Test manual and AI control.

· Safety: Emergency cutoff, parachute deployed manually.

· Pass criterion: Pilot can hold stable hover and perform simple turns.

Stage 6 -- Free Flight (Low Altitude, Remote Area)

· No catapult -- use sequenced slow lift from engines.

· Altitude: Start at 10 ft, gradually increase.

· Backup: Parachute + emergency battery.

· Pass criterion: Controlled flight for 2 minutes, safe landing.

Stage 7 -- Full Envelope Testing

· Add sensors: IMU, barometer, pitot, cameras.

· AI training: On real flight data.

· Goal: Hands‑free Superman pose steering for entire flight.

\-\--

4\. Go/No‑Go Abort Criteria (Time & Money Based)

Stage Minimum Success Threshold If Not Met

Stage 0 Control loop runs at 50 Hz with \<100 ms latency Refine code or
faster processor

Stage 1 Tesla valve reverse leakage \>40% Redesign geometry

Stage 2 Thrust \<0.1 N per cm² Try richer mixture; if still low, abort
concept

Stage 3 Thrust \<2 N/cm² or fuel consumption \>10 g/min per N Abort --
engine too inefficient

Stage 4 Vector moment \<10% of max thrust Increase tube spacing; if
still low, abort

Stage 5 Pilot reports any burn or structural vibration Redesign
backplate insulation

Stage 6 Parachute fails in any test Immediate abort

\-\--

5\. Open Items for Team Discussion

1\. Dry water synthesis: Can we make consistent batches with a kitchen
blender and fumed silica? Test needed.

2\. Lime clogging: Run Stage 2 for 10 minutes continuous. If clog stops
fuel flow, design an agitator or replaceable reactor liner.

3\. Noise: At 100+ dB, we need hearing protection and remote operation
for initial tests.

4\. Legal test site: Knox Makers should partner with a private landowner
or a remote desert location (e.g., Nevada).

\-\--

6\. Final Note from the Author

"I'm baked, my memory glitches, but the physics is straight. Build the
small tube first. Let the data tell you if I'm crazy. I'm probably not."

--- Eric McElroy

\-\--

End of Addendum

This document is public prior art. No patents. Build freely.
