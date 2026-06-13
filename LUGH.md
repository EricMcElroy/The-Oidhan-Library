![](media/image1.png){width="7.933590332458443in"
height="4.323231627296588in"}

![](media/image2.png){width="4.322916666666667in"
height="4.322916666666667in"}

**LUGH**

*Temporal Craft Reconstruction via Off-the-Shelf Sensor Fusion and
Haptic Playback*

**Author:** Eric Don McElroy\
**Date:** 2026-06-09\
**Contact:**
[[eric.mcelroy@gmail.com]{.underline}](mailto:eric.mcelroy@gmail.com) \|
[[https://substack.com/@eskamick]{.underline}](https://substack.com/@eskamick)\
**Version:** 1.0\
**Status:** Public Release / Prior Art Disclosure

## Abstract

LUGH is a system that reconstructs the exact physical making of a
historical metal artifact---capturing hammer strikes, body mechanics,
thermal history, and environmental context---and replays it as an
immersive, standalone VR experience viewable on a consumer headset. The
system fuses data from off-the-shelf sensors, runs a one-time physics
retrodiction, and outputs a pre-rendered 3D scene requiring no host PC
at playback. A blacksmith or museum visitor can stand inside the
reconstruction and watch a dead craftsperson\'s hands move. The minimum
playback hardware is a Meta Quest 3. All sensor components are
commercially available. No custom fabrication is required. Haptic
modules are additive, not essential to the core experience.

## Problem

Museums and cultural institutions preserve artifacts but cannot preserve
the *making* of those artifacts. The thermal, kinetic, and muscular
reality of craft---the hammer\'s arc, the fire\'s breath, the smith\'s
fatigue---is lost. Current practice captures surface geometry and
chemical composition but cannot reconstruct the sequence of physical
actions that produced the object. Intangible craft heritage remains
intangible. A blacksmith studying a historical candle holder can measure
its dimensions and guess at its production, but cannot witness the
production itself.

## Concept

LUGH inverts the problem. Instead of analyzing the artifact as a static
end state, the system treats it as a physical record of the forces that
made it. A sensor array captures surface topology, subsurface structure,
elemental composition, and tool mark geometry. A physics engine runs
backward from that data, solving for the hammer strike sequence, hand
position, body posture, and thermal environment that would have produced
the observed result. The solved sequence is rendered once as a 3D
environment and played back on a standalone VR headset. The user
observes the smith at work. Optional haptic gloves and force-feedback
arms allow the user to grip the hammer and feel the strike.

The core insight: this is not a real-time simulation. It is a one-time
reconstruction and a one-time render. Compute time is unconstrained. A
three-day render is acceptable. The playback file is a static asset,
distributable like a video.

## Feasibility

Every component in LUGH already exists and is deployed in industrial,
medical, or museum contexts. The novelty is integration, not invention.

**Sensor Fusion Layer:** Photogrammetry, structured light scanning,
handheld X-ray fluorescence (XRF), digital microscopy, and thermal
imaging are all mature, off-the-shelf technologies. Industrial CT and
laser profilometry are available via rental or service bureau for
higher-resolution subsurface data. None of this hardware is
experimental.

**Physics Retrodiction Layer:** Finite element analysis (FEA) software
packages such as Ansys, Abaqus, and open-source alternatives can solve
for the deformation history of a metal object given its final geometry
and material properties. Inverse kinematics solvers, common in game
engines and biomechanics, can reconstruct body posture from hand
position data. The physics is well understood. The compute cost is a
workstation and patience.

**Playback Layer:** The Meta Quest 3 is a \$500 standalone device
capable of rendering high-fidelity, pre-lit 3D environments without a
host PC. Haptic gloves (SenseGlove, HaptX) and force-feedback arms
(Haption, Virtuix) exist as off-the-shelf peripherals. None require
custom engineering.

**Precedent:** Conservation science already uses CT, XRF, and
photogrammetry on artifacts. Biomechanics labs already perform inverse
kinematics from kinematic markers. The pieces are in production. LUGH
connects them.

## Challenges

**Sensor fusion and calibration:** Different sensor modalities produce
data at different scales and coordinate systems. Coregistration of CT
volumes, surface meshes, and XRF point spectra into a single model
requires careful calibration and alignment algorithms. This is a
software integration problem, not a hardware gap. Existing medical
imaging and industrial metrology pipelines solve similar problems
routinely.

**Solving the strike sequence:** Determining the order and force of
hammer strikes from final surface deformation is a partial differential
equation inverse problem. Prior art exists in forensic tool mark
analysis and manufacturing quality control (tracing a machined surface
back to the tool path). For a hand-forged object, the solution space is
large but constrained by material behavior, hammer geometry, and human
biomechanics. A close approximation is achievable. Perfect
reconstruction is not the goal---a convincing and informative
reconstruction is.

**Thermal history from oxide layers:** Oxide color and thickness
correlate with temperature and atmosphere in the forge. This
relationship is well characterized in metallurgy. Extracting
quantitative thermal history from oxide spectroscopy is a matter of
applying existing calibration curves. Some uncertainty will remain,
particularly for artifacts that have corroded. The system reports
confidence intervals, not false precision.

**Haptic fidelity:** Electrical stimulation for texture rendering and
force-feedback for weight simulation are active areas of commercial
development. Current haptic gloves provide convincing but imperfect
feedback. The LUGH architecture treats haptics as an upgrade path. The
core visual experience is unimpaired by haptic limitations.

**Institutional inertia:** Museums may be slow to adopt a new workflow.
The counterargument is that LUGH requires no change to existing
conservation practice. The sensors are the same ones already pointed at
artifacts. The output is a public-facing exhibit product that museums
already want: immersive visitor experiences.

## Development Path

**Phase 1 -- Sensor Prototype:** Partner with a working blacksmith to
produce a candle holder using documented techniques. Scan the artifact
with photogrammetry, XRF, and digital microscopy. No subsurface data.
Reconstruct the strike sequence and thermal history. Render a
proof-of-concept VR scene. Validate against the documented production
method.

**Phase 2 -- Museum Pilot:** Approach a museum with existing CT and XRF
capability. Select a historical metal artifact with visible tool marks.
Perform full sensor fusion, including subsurface data. Produce a LUGH
reconstruction. Measure accuracy against conservator knowledge. Deploy
playback on Quest 3 in a visitor-facing setting.

**Phase 3 -- Haptic Integration:** Add haptic glove support for grip and
texture. Integrate force-feedback arm for hammer-weight simulation.
Offer as an add-on module for institutions with budget. Maintain Tier 0
(Quest-only) as the baseline.

**Phase 4 -- Open Repository:** Publish the sensor-to-render pipeline as
open documentation. Allow any museum or blacksmith to submit artifact
data and receive a LUGH reconstruction. Build a public library of craft
reconstructions accessible via Quest store or direct download.

## Technology Stack

All components are real, commercially available, and cited by product
name or manufacturer where applicable.

### Sensor Hardware (Two Tiers)

  ------------------------------------------------------------------------
  **Component**     **Tier 1           **Tier 2          **What It
                    (Minimal)**        (Enhanced)**      Captures**
  ----------------- ------------------ ----------------- -----------------
  Surface geometry  DSLR               Laser             Tool marks,
                    photogrammetry +   profilometry      strike depth,
                    RealityCapture     (Keyence VR-6000, wear patterns
                                       Faro arm)         

  Elemental         Handheld XRF       Benchtop XRF +    Metal type, scale
  composition       rental (Bruker S1  XRD (Bruker M4    chemistry, oxide
                    Titan)             TORNADO)          phases

  Subsurface        Not available at   Industrial CT     tome
  structure         Tier 1             rental (GE        
                                       Phoenix V         

  Tool mark         Dino-Lite Edge     Environmental SEM Strike
  microscopy        AM7915MZT          (museum)          directionality,
                                                         surface grain

  Thermal history   IR thermometer /   High-speed        Forge and quench
                    FLIR One Pro       thermal camera    temperatures
                                       (FLIR X6900sc)    (requires live
                                                         demo burn)

  Body mechanics    Inverse kinematics Rokoko SmartSuit  Body posture
                    from strike angles Pro II mocap      solution and
                                       (modern smith)    training data
  ------------------------------------------------------------------------

**Tier 1 sensor cost:** \~\$3,200--\$4,000 (plus one-time XRF rental)\
**Tier 2 sensor cost:** \~\$8,000--\$12,000 (plus rental days for CT,
XRD, thermal)

### Compute Options

  ------------------------------------------------------------------------
  **Option**        **Spec**          **Cost**           **Notes**
  ----------------- ----------------- ------------------ -----------------
  Cloud compute     Lambda Labs /     \$200--\$500 total Photogrammetry,
  only              Paperspace GPU                       physics sim, and
                    instances                            render run
                                                         remotely. No
                                                         local PC
                                                         required.

  Used local        i7-13700K, RTX    \$1,200--\$1,800   Runs all software
  workstation       3080, 32GB RAM,                      locally.
                    2TB NVMe                             Multi-day renders
                                                         acceptable.

  New local         i9-14900K, RTX    \$4,000--\$5,000   Faster iteration.
  workstation       4090, 64GB RAM,                      Required for Tier
                    4TB NVMe                             2 CT data
                                                         processing.
  ------------------------------------------------------------------------

### Playback Hardware (Three Tiers)

  ----------------------------------------------------------------------------
  **Tier**          **Hardware**      **Cost (USD)**         **Experience**
  ----------------- ----------------- ---------------------- -----------------
  **0 -- Watch      Meta Quest 3      \$350--\$500           Fully immersive
  Only**            (128GB)                                  visual
                                                             reconstruction.
                                                             Walk around the
                                                             smithy. Watch the
                                                             hammer strikes
                                                             from any angle.
                                                             No PC required at
                                                             playback.

  **1 -- Basic      Quest 3 +         \~\$4,000--\$5,000     Add grip and
  Haptics**         SenseGlove Nova                          texture feedback.
                    (used)                                   Feel the hammer
                                                             handle.

  **2 -- Full       Quest 3 +         \~\$25,000--\$35,000   Feel hammer
  Haptics**         SenseGlove Nova                          weight, impact
                    2 + Haption                              shock, and anvil
                    Virtuose 6D                              ring through full
                    force-feedback                           6DOF force
                    arm                                      feedback.
  ----------------------------------------------------------------------------

### Software Stack

-   Photogrammetry: RealityCapture, Meshroom (open source)

-   Physics simulation: Ansys / Abaqus / CalculiX (open source FEA)

-   Inverse kinematics: Blender IK rig, custom Python solver

-   Environment rendering: Unreal Engine 5 or Blender (Cycles),
    > single-frame pre-render

-   VR playback: Unity or Unreal Engine build for Quest 3 standalone APK

## Author Note

This document serves as prior art disclosure. The LUGH system is
released into the public domain. Any individual, institution, or company
is free to build, modify, deploy, or commercialize the system without
restriction.

Attribution to Eric Don McElroy is appreciated but not required.

The design is named for Lugh, the many-skilled god of Celtic mythology.
The system\'s purpose is to democratize access to the making of
things---to let any craftsperson stand beside the dead and learn from
their hands.

Build it. A blacksmith with a Quest 3 and access to a museum\'s scan
data can walk into a 14th-century workshop before the decade ends. The
sensors exist. The compute exists. The headset costs five hundred
dollars. The only remaining component is the will to integrate them.

If you are a museum conservator, a VR developer, a haptics engineer, or
a craftsperson with access to artifacts: the specifications above are
sufficient to begin. No patents encumber this design. No licensing is
required.
