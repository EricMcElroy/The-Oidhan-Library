# **Predictive Terrain-Aware Dual Self-Balancing Mobility Platform**

### **Real-time predictive terrain sensing and distributed dual-axis active balancing for stable, high-CoM wearable transit.**

**Author:** Eric Don McElroy\
**Date:** 2026-06-07\
**Contact:** Eric.McElroy@gmail.com / https://eskamick.substack.com/\
**Version:** 1.0\
**Status:** Public Release / Prior Art Disclosure

## **Abstract**

Conventional powered roller skates apply forward thrust at ground level,
well below the rider\'s center of mass, generating destabilizing
backward torque that causes violent falls. This platform addresses this
fundamental vulnerability by integrating **independent dual-axis (pitch
and roll) active balancing directly into a dual-wheel boot chassis**,
coupled with **real-time predictive terrain sensing**. A centralized,
body-worn processing unit fuses data from forward-looking solid-state
LiDAR, stereo vision, and tactile edge tracking to pre-compensate for
topographic changes *before* they destabilize the rider. The result is a
wearable robotic system that treats the ground ahead as a continuous
data stream, converting a mechanical hazard into a highly predictable,
intuitive extension of locomotive intent.

## **Problem Statement**

Conventional powered roller skates suffer from a fundamental mechanical
deficit: **thrust is applied at ground level, well below the rider\'s
center of mass (CoM)**. This creates a destructive torque vector:

\$\$\\tau = F \\times h\_{\\text{CoM}}\$\$

When accelerating, this low-thrust line violently forces the feet
forward while pulling the upper body backward. Because these systems
lack a rigid handlebar or mechanical lever, the rider has no physical
means to counter the rotational force. Existing safety measures are
purely **reactive**---the rider must actively lean forward or begin
falling before the system registers and applies corrective power. On
uneven terrain or during rapid direction changes, this lag is
insufficient to prevent loss of balance.

## **Concept Overview**

This mobility platform transforms a pair of independent powered boots
into a **synchronized, predictive, wearable robotic system**. The
architecture consists of three distinct operational layers:

\[Boot Sensors: LiDAR / Vision / IMU\] ──\> \[Deterministic Wired Bus\]
──\> \[Central Belt Pack Processor\]

│

┌─────────────────────────────────────────────────────────────────────────┘

▼

\[Lookahead Terrain Preview Map\] ──\> \[Predictive Torque / Pitch
Adjustments\] ──\> \[Synchronized Hub Motors\]

**Layer 1: Kinematic Base\
** Each boot features two side-by-side drive wheels containing
**integrated hub motors**, establishing a stable, self-balancing
inverted pendulum base for each foot. The footplate features **active
pitch articulation** to dynamically alter the rider\'s relative shin
angle, allowing real-time tilt compensation independent of upper body
movement.

**Layer 2: Coordination & Processing\
** Power and high-bandwidth deterministic data are offloaded via a
**retractable, shielded breakaway cable** to a centralized, body-worn
waist pack. This pack acts as the master processing node, continuously
averaging rider pitch and roll intent between both feet to prevent the
two independent platforms from diverging into opposing torque vectors.

**Layer 3: Predictive Perception\
** Instead of reacting to a destabilizing event *after* it occurs, boot
toe caps feature **downward-angled flash LiDAR and stereo vision
modules**. These sensors continuously map the micro-topography of the
ground 0.2 to 1.0 meters ahead, feeding a short-horizon digital
elevation model back to the central controller to **adapt the drive
profile before the wheels make physical contact** with an obstacle.

## **Why This Works --- Feasibility Basis**

The system treats the rider and dual independent boots as a **coupled,
multi-axis inverted pendulum**. By maintaining a continuous state
estimation loop running at ≥200 Hz, the hub motors deliver predictive,
precise acceleration to keep the wheels positioned directly beneath the
rider\'s dynamic center of pressure.

**Feed-Forward Terrain Compensation:\
** When the predictive perception layer identifies an oncoming incline
or step, the system calculates the required torque adjustment ahead of
time. Rather than relying entirely on error-driven feedback from a
standard PID controller, the system incorporates a **feed-forward
control term** based on upcoming terrain slope
(\$\\theta\_{\\text{terrain}}\$):

\$\$\\tau\_{\\text{motor}} = \\tau\_{\\text{feedback}} + k\_{\\text{ff}}
\\cdot \\theta\_{\\text{terrain}}\$\$

By injecting the terrain profile directly into the torque calculation
loop, the system **pre-tilts the footplate forward and ramps up motor
torque *prior* to hitting an incline**. This cancels out the
deceleration-induced inertial lag that would normally throw the rider\'s
upper body forward during flat-to-uphill transitions.

**Dual-Boot Synchronization:\
** Each boot independently balances its respective foot section using a
local 9-axis IMU and motor feedback loop. The central processor runs a
**consensus algorithm** that enforces roll and pitch alignment between
the two platforms, preventing asymmetric collapse during dynamic
maneuvers. If communication latency exceeds the control loop period (5
milliseconds), the system automatically enters a high-damping safety
mode, reducing speed and motor responsiveness to prevent leg-tearing
divergence.

**Inverted Pendulum Stability:\
** A dual-wheel configuration per boot provides a baseline of stability
that a single-wheel design cannot achieve. The wheels themselves act as
the \"stick\" of the inverted pendulum; the rider\'s body mass and CoM
act as the \"bob.\" Active motor torque is the stabilizing force. At 200
Hz control loop frequency, the system can recover from perturbations far
faster than human reflexes alone.

## **Known Engineering Challenges**

-   **Ego-Motion Subtraction and Point Cloud Jitter:** Because sensors
    > are mounted directly to the feet, walking, striding, and road
    > vibrations introduce massive high-frequency noise into optical and
    > LiDAR tracking data. Resolving this requires **extremely
    > low-latency visual-inertial odometry (VIO)** to cleanly subtract
    > boot movement from environmental point clouds. Failed VIO
    > alignment cascades into terrain miscalculation and unpredictable
    > motor corrections.

-   **Deterministic Dual-Agent Convergence:** If the communication line
    > between the two boots experiences latency or packet loss, the
    > skates can act independently, tearing the rider\'s legs apart or
    > creating opposing torque vectors that cause immediate falls. The
    > system demands a **deterministic protocol with microsecond-level
    > clock synchronization**, typically implemented via high-speed
    > CAN-FD or custom timing synchronization over a wired breakaway
    > cable.

-   **Traction Dynamics on Variable Substrates:** Transitioning suddenly
    > from high-friction dry asphalt to low-friction surfaces---wet
    > metal, loose gravel, ice---causes sudden wheel slippage. This
    > invalidates the inverted-pendulum control assumptions and risks
    > motor over-spin, requiring **immediate slip detection and
    > microsecond-level torque dampening**. Algorithmic wheel-slip
    > detection must distinguish between intentional drift maneuvers and
    > uncontrolled skid.

-   **Sacrificial Edge Protection:** Foot-mounted sensors operate within
    > a harsh boundary layer with continuous exposure to water, mud,
    > flying stones, and direct physical curb impacts. Robust
    > **hydrophobic sapphire glass shielding and sacrificial tactile
    > bumpers** are essential to prevent premature sensor failure.

-   **Human Locomotive Inference:** Translating human balance
    > intent---how a rider naturally shifts weight to initiate turns or
    > brake---into motor commands requires real-time disambiguation
    > between intentional maneuvers and instability compensation.
    > Over-aggressive feedback correction can cause oscillation;
    > under-responsive correction invites falls.

## **Suggested Development Path**

**Phase 1: Single-Boot Gyroscopic Rig**

-   Build a single-boot testing platform locked within a vertical guide
    > rail assembly.

-   Program the 2-axis IMU feedback loop to balance a variable
    > dead-weight payload.

-   Validate core stick-slip and inverted-pendulum recovery algorithms
    > against sudden external physical shoves.

-   Measure control loop latency and settle time under worst-case
    > perturbation profiles.

**Phase 2: Off-Line Terrain Feed-Forward Tracking**

-   Mount a prototype toe-cap sensor suite onto a non-powered test
    > skate.

-   Roll the assembly over structured obstacles (cords, speed bumps,
    > ramps) to refine visual-inertial odometry algorithms.

-   Verify that the system generates clean digital elevation maps under
    > real-world vibration profiles.

-   Establish baseline LiDAR/vision fusion filtering parameters for the
    > lookahead terrain map.

**Phase 3: Dual-Boot Integrated Prototyping**

-   Assemble a complete functional prototype with two fully actuated
    > boots connected to a central processing belt pack.

-   Implement restricted software safety profiles (low speed limits,
    > high damping factors) alongside a physical safety harness.

-   Map out and fine-tune user intent translation during turning,
    > coasting, and braking maneuvers.

-   Conduct controlled field trials on varied terrain (flat, inclines,
    > stairs, textured surfaces) to validate real-world control
    > convergence.

## **Why Now**

The realization of a predictive, wearable mobility platform is enabled
by **three converging technology trends:**

-   **Ultra-Compact Solid-State LiDAR & ToF Sensors:** Flash LiDAR and
    > time-of-flight camera modules originally designed for mobile
    > handsets and micro-drones are now commercially available in
    > compact, power-efficient form factors. These sensors offer
    > millimeter-level range precision over short horizons without
    > mechanical moving parts.

-   **High-Torque Density Hub Motors:** Brushless outrunner hub motors
    > developed for the light electric vehicle (LEV) industry provide
    > necessary rotational force within a compact wheel footprint,
    > enabling self-contained boot actuation.

-   **Edge-Compute Availability:** Modern edge-compute modules can
    > handle high-frame-rate spatial tracking, visual-inertial odometry,
    > and neural-network-driven surface categorization entirely locally
    > within a compact battery budget. Processing no longer requires
    > offloading to a cloud endpoint, eliminating latency and improving
    > determinism.

The convergence of these three shifts makes a **predictive, distributed
wearable robotic system feasible and economically viable** for the first
time.

## **Appendix: Available Technology & Prior Art**

  -------------------------------------------------------------------------
  **Item**          **Description**              **Source / Availability**
  ----------------- ---------------------------- --------------------------
  Solid-State Flash Compact, non-mechanical      PMD Technologies,
  LiDAR / ToF       depth sensors;               STMicroelectronics,
  Sensors           millimeter-level range       Infineon, Qualcomm.
                    precision over short         
                    horizons (0.1--5 m).         

  High-Torque       External-rotor outrunner     Electric skateboard
  Brushless Hub     motors integrated directly   suppliers (Evolve,
  Motors            inside standard 100--150 mm  Boosted); micro-mobility
                    wheel hubs; 500--1000 W      component distributors.
                    power range.                 

  Deterministic     High-speed serial bus        Automotive and industrial
  CAN-FD            controllers with             robotics suppliers (NXP,
  Transceivers      hardware-level error         STMicroelectronics,
                    correction and microsecond   Bosch).
                    clock synchronization.       

  High-Rate 9-Axis  Low-noise MEMS incorporating Bosch Sensortec,
  IMUs              triaxial accelerometers,     Invensense (TDK), Xsens;
                    gyroscopes, and              drone and mobile device
                    magnetometers; 200+ Hz       suppliers.
                    sampling rates.              

  Visual-Inertial   Open-source frameworks       Published research; GitHub
  Odometry (VIO)    (ORB-SLAM3, Basalt, SVO) for repositories; robotics
  Algorithms        real-time ego-motion         middleware (ROS).
                    subtraction from noisy       
                    sensor streams.              
  -------------------------------------------------------------------------

**Additional references and prior art worth reviewing:**

-   \"Control and Optimization Strategy for Multi-Axis Split-Platform
    > Self-Balancing Vehicles\" --- *International Journal of Mobile
    > Robotics*

-   \"Real-Time Visual-Inertial Odometry and Terrain Mapping under
    > High-Vibration Foot-Mounted States\" --- *IEEE Sensors Journal*

-   Segway and Hoverboard self-balancing platform architectures
    > (single-axis gyroscopic stabilization prior art)

-   Powered exoskeleton dual-foot coordination frameworks (military and
    > medical mobility literature)

-   Autonomous wheeled robot terrain prediction and adaptive control
    > models (field robotics literature)

## **Author Note**

The classic failure mode of powered skates isn\'t a lack of motor
power---it\'s a fundamental **deficit in physical leverage**. A
handlebar provides mechanical advantage; wearable skates have none. By
migrating the core compute layer to a centralized body pack and treating
the ground ahead as an **unrolled data stream**, we can use software to
solve what was previously viewed as an unmanageable mechanical hazard.
The predictive layer is the critical insight: by *looking ahead* rather
than *reacting to what has already happened*, the system converts a
fundamentally unstable mechanical platform into a highly predictable,
intuitive extension of human locomotive intent.

*This document is released as a public prior art disclosure. The author
asserts origination of the concept as described herein as of the date
above. No patent is claimed. Builders are free to develop, implement,
and commercialize this concept without restriction or licensing
requirement. Attribution appreciated but not required.*

*© Eric Don McElroy --- Released to the public domain.*
