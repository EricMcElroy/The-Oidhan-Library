Title: A Low‑Cost, Privacy‑First Wearable with On‑Device Reinforcement
Learning for Animal Health Intervention

Author: Eric Don McElroy

Date: 2026-06-11

Contact: Knoxville, TN

Version: 1.0 -- Public Release / Prior Art Disclosure

\-\--

Abstract

A \$40 wearable -- built from an ESP32‑S3, IR thermopile, accelerometer,
microphone, and edge‑blurred camera -- can detect early signs of illness
in animals. But detection is only half the problem. This paper
introduces two technical advances that turn a passive sensor collar into
an active, adaptive intervention system:

1\. An on‑device reinforcement learning loop that speaks to the pet in
the owner's voice, training the animal to rest or settle when early
symptoms (lameness, cough, pain posture) appear.

2\. An adaptive radio stack (BLE → LoRa → LTE‑M) that maintains
connectivity from house to pasture to lost‑pet scenario, while a modular
form factor scales the same electronics from a cat's breakaway ID tag to
a cow's ear tag.

All processing is local. No cloud is required. Privacy is preserved by
edge‑blurring humans from the camera stream. The system is buildable
today with off‑the‑shelf parts. This paper provides the architecture;
two companion papers apply it to pet health (Paper 1) and
insurance/industry disruption (Paper 2).

\-\--

1\. Hardware Platform -- One Core, Many Bodies

The same 28 mm × 28 mm core PCB carries all sensing and compute. It is
then potted or enclosed for three physical carriers:

Carrier Target Weight Key Modifications

Collar Puck Dogs \>10 kg, equipment 40 g Full sensor suite (camera
enabled)

ID Tag Module Cats, rabbits, small dogs 15 g Breakaway strap, camera
disabled, IR+accel+mic only

Ear Tag / Leg Band Livestock (cattle, sheep, goats) 35 g IP69K
overmolding, high‑impact, replaceable battery every 6 months

Common components (per unit, 1k+ qty):

Component Cost Function

ESP32‑S3 module \$8 Dual‑core Xtensa, 512 KB SRAM, WiFi/BT, local AI

MLX90614 IR thermopile \$10 Non‑contact temperature (ear/base)

MPU6050 6‑axis accelerometer \$3 Gait, posture, respiratory rate, heart
rate (ballistocardiography)

SPH0645 microphone \$2 Cough, bark, snore, response to voice commands

OV2640 camera \$6 Posture, gait, eye/nose discharge -- edge‑blurred for
privacy

MAX98357 + small speaker \$4 Plays owner's pre‑recorded phrases

500 mAh Li‑Po + charger \$6 3--7 days normal operation

Enclosure & strap \$5 Varies by carrier

Total mass production \~\$44 Falls to \$20--25 at 10k+ units

All software is free (TensorFlow Lite Micro, Espressif IoT Development
Framework, custom RL kernel).

\-\--

2\. Adaptive Radio Stack -- From Living Room to Lost Pet

A single radio cannot serve every scenario. The ESP32‑S3 manages three
radio modes, sleeping most of the time:

Mode Trigger Radio Power Consumption Range Use Case

Home (short) Connected to home WiFi/BLE BLE 5.0 (Coded PHY) 5 mA average
100 m line‑of‑sight Daily indoor/backyard

Away (medium) No home network for 10 min + pet moving (accel) LoRa
(SX1262 add‑on) 15 mA burst, 0.5 mA sleep 2--5 km Pasture, neighborhood
search

Emergency (long) Lost + anomaly detected (e.g., fever, distress bark)
LTE‑M (cellular IoT, e.g., SARA‑R5) 150 mA burst, 50 mA to attach
Unlimited Lost pet, medical crisis

Dead zone No network after 30 min Local flash logging 0.1 mA N/A Data
saved until reconnection

Key design rule: The long‑range radios are not always on. The collar
attempts BLE first. If that fails and the accelerometer indicates
movement (pet is not sleeping on the couch), it escalates. Anomaly
detection further raises priority. This yields 3--7 days battery life in
normal mixed use.

Offline sync: If the collar enters a dead zone during an anomaly, it
logs IR, accel, and audio snippets to onboard flash (2 MB, enough for 24
hours of compressed summaries). Once home WiFi is restored, the log
uploads automatically. No data is lost.

\-\--

3\. On‑Device Reinforcement Learning -- The Active Voice Loop

Detection alone is passive. The collar can intervene by speaking to the
pet in a 2--5 second pre‑recorded phrase from the owner's voice (e.g.,
"Lie down," "Come here," "Easy").

3.1 The Intervention Loop

1\. Anomaly is detected (e.g., lameness score \>0.7, cough frequency
\>5 /hr).

2\. Collar waits a learned offset (see below), then plays the selected
phrase.

3\. Microphone + accelerometer monitor the pet's response over the next
30 seconds:

· Positive: Reduced lameness, settled posture, cessation of coughing.

· Neutral: No change.

· Negative: Increased restlessness, escape behavior, distress
vocalization.

4\. A tiny reinforcement learning model (policy gradient, \~20 kB)
updates two parameters for that anomaly type:

· Phrase index (which of 3--5 owner phrases to use)

· Timing offset (how many seconds after anomaly to play it)

No cloud, no manual labeling. The collar learns what calms this specific
animal over days.

3.2 Why This Is Not a Toy RL Problem

Benchmark (CartPole, Atari) Real Pet Collar

Immediate reward per step Reward sparse (pet settles minutes later)

Stationary environment Pet's age, mood, time of day change baseline

Full state observability Partial -- no video of owner or environment

Unlimited memory 20 kB model, no replay buffer

This is a real‑world, non‑stationary, partially observable,
sparse‑reward RL problem on \$15 of silicon. It has no existing
benchmark. That is exactly why it interests researchers.

3.3 Privacy and Safety

· The collar never records or transmits human speech (microphone listens
only for pet vocalizations and response to command).

· All RL updates happen on‑device. No cloud profile of the pet is
created unless owner explicitly opts into anonymized research sync.

· The speaker volume is limited (\<85 dB) to avoid startling the animal.

\-\--

4\. Open Research Questions (For Academics)

The system works as a prototype. To become robust, these questions need
investigation:

1\. Sparse reward convergence -- How many intervention trials are needed
for stable policy improvement in dogs vs. cats vs. livestock?

2\. Non‑stationarity -- How does the model adapt when the pet ages or
develops chronic pain? Does retraining from scratch outperform
continuous online learning?

3\. Transfer learning across species -- Can a model pretrained on 100
dogs be fine‑tuned on a cat with only 10 interventions?

4\. Radio scheduling for scale -- What is the optimal wake/sleep pattern
for 200 ear tags in a feedlot, given LoRa collisions and battery
constraints?

5\. Verification without vet -- Can the collar's own sensor recovery
(temperature normalization, gait improvement) serve as "automated
verification" for insurance discounts? (See Paper 2.)

\-\--

5\. Related Papers

This architecture is the technical foundation for two companion papers
that focus on applications:

· Paper 1: The Proactive Pet Health Loop -- Early detection, veterinary
verification, and owner alert in a familiar voice. Focuses on animal
welfare and at‑home monitoring.

\[Link or note: attached separately\]

· Paper 2: The Proactive Risk Loop -- How the same collar architecture
disrupts pet insurance, human health insurance, livestock insurance,
industrial maintenance, and auto insurance through verifiable proactive
behavior.

\[Link or note: attached separately\]

Readers interested in clinical outcomes or economic disruption should
refer to those papers. This paper provides the hardware and edge‑AI
details for both.

\-\--

6\. Build It Yourself

All designs are released to the public domain. To build a prototype:

1\. Order the components listed in Section 1 (≈\$65 one‑off).

2\. Flash the ESP32‑S3 with TensorFlow Lite Micro and the open‑source
anomaly detection models (available on GitHub under the same name).

3\. Record three phrases in your own voice: "Come here," "Lie down,"
"Easy."

4\. Attach to your pet's collar. Within one week, the RL loop will begin
adapting.

No patents. No trademarks. No permission needed. Build, verify, share.

\-\--

This document is released to the public domain. Attribution appreciated
but not required.

\-\--

That\'s the full Paper 3. You can now:

· Copy‑paste this into a new document.

· At the bottom of your existing Paper 1 and Paper 2, add a short
\"Related Paper\" section pointing to this one (similar format, just one
line each).

· Send all three to professors, each as a separate attachment or linked
PDF.
