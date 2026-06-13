CLINICAL TWIN PLATFORM

A passive, sensor-equipped exam room that captures multimodal patient
data during routine visits, building a longitudinal digital baseline for
personalized medicine and early drug-effect detection.

Metadata

· Author: Eric Don McElroy

· Date: 2026-06-09

· Contact: eric.mcelroy@gmail.com, https://substack.com/@eskamick

· Version: 1.0

· Status: Public Release / Prior Art Disclosure

\-\--

Abstract

The Clinical Twin Platform transforms a standard medical exam room into
a continuous, passive sensing environment. A suite of low-cost,
unobtrusive sensors---load cells in the chair, a pressure-sensitive
floor mat, high-resolution visual and thermal cameras, a microphone
array, and optional EEG/EKG headband---captures weight distribution,
posture, gait, skin temperature patterns, vocal biomarkers, and cardiac
rhythm without altering the doctor-patient interaction. The doctor views
fused sensor overlays through an AR monocular, seeing thermal maps, UV
fluorescence, and change-from-baseline alerts in real time as they
examine the patient. All data streams are timestamped, encrypted, and
merged with traditional bloodwork and imaging results to create a "visit
vector." Over successive visits, these vectors form a longitudinal,
high-resolution digital twin of the patient. When a new drug is
prescribed, the platform detects subtle deviations from the patient's
personal baseline---posture shifts, temperature changes,
micro-movements---flagging side effects or efficacy signals earlier than
conventional methods. The system is designed for a cost point that
allows installation in every exam room in a clinic, using commodity
sensors and a single local edge server.

\-\--

Problem

Routine medical exams generate a wealth of incidental data that is never
captured: how a patient walks into the room, how they hold themselves
while seated, the warmth of their skin, the frequency of their cough,
the tremor in their voice. A physician relies on memory and isolated
vital signs to track a patient over time, missing subtle patterns that
could indicate early drug side effects, disease progression, or
recovery. When a new medication is prescribed, the baseline for
comparison is often a sparse set of measurements---blood pressure,
weight, heart rate---taken at the very visit where the drug is
initiated, leaving no true pre-drug reference. Simultaneously, clinical
trials for new pharmaceuticals struggle to detect nuanced physiological
effects that fall outside pre-specified endpoints. A tool that builds a
rich, objective, personal baseline during routine care---and then
measures against it at every subsequent visit---would transform both
individual treatment and drug development.

\-\--

Concept

The Clinical Twin Platform is a modular sensor array integrated into the
furnishings and infrastructure of a standard exam room. No sensors are
worn by the patient beyond an optional lightweight headband for a brief
EEG/EKG capture. The system operates passively, requiring no change in
physician workflow.

Sensor Suite (core):

· Chair sensors: Strain gauge load cells under the seat and armrests
capture weight, weight distribution, and ballistocardiographic signals
(heart rate, respiratory rate via mechanical coupling through the arms).
Capacitive sensors in the armrests add contactless electrodermal
activity and subtle movement tracking.

· Floor mat: A pressure-sensitive mat captures weight, balance, and gait
dynamics as the patient walks in and stands for initial assessment. A
quick footprint pressure map is generated.

· RGB camera array: Two synchronized, high-resolution cameras mounted
near the ceiling capture full-body posture, visible skin lesions,
pallor, facial expressions, and eye movements. The cameras are
positioned to avoid the physician's work area.

· Thermal camera: A long-wave infrared camera mounted alongside the RGB
cameras maps skin temperature distribution in real time, highlighting
asymmetrical inflammation, fever, and circulatory anomalies.

· Microphone array: Directional MEMS microphones capture voice
characteristics, cough type and frequency, breathing sounds, and speech
cadence. On-device machine learning models extract relevant biomarkers
without recording raw audio.

· Pulse oximeter / blood pressure cuff (networked): Existing devices in
the room feed their readings directly into the system via Bluetooth,
eliminating manual data entry.

Extended sensors (optional, per room upgrade):

· EEG/EKG headband: A dry-contact, quick-fit headband captures a
30-second electroencephalogram and electrocardiogram snapshot during the
exam, adding neurological and cardiac rhythm data to the visit vector.

· Breath sniffer: A small metal-oxide sensor near the patient's head
captures volatile organic compound (VOC) profiles from exhaled breath,
providing a broad chemical signature that can be trended over visits.

· UV illumination: A switchable UV LED panel allows the physician to
highlight skin conditions (fungal, bacterial, pigmentation) while the AR
monocular overlays the UV image with enhanced contrast.

Physician Interface:

The physician wears a lightweight AR monocular (or uses a tablet
display) that projects sensor-derived overlays directly onto their view
of the patient. Thermal maps appear as gentle color washes on the skin;
detected asymmetries are highlighted; change-from-baseline metrics for
this patient are displayed as subtle icons near relevant body regions.
The physician can toggle views---thermal, UV, motion, past-visit
comparison---with voice commands or a small finger ring. The monocular
preserves direct eye contact and keeps both hands free for palpation and
examination. The physician's tablet simultaneously logs structured
observations (pain on palpation, range of motion, swelling) via a simple
touch interface, converting subjective clinical findings into
machine-readable fields.

Data Fusion and Longitudinal Record:

All sensor streams are timestamped and fused on a local edge server in
the clinic. After each visit, the system generates a "visit vector"---a
structured, multi-dimensional snapshot of that encounter. Blood work and
imaging results, typically arriving days later, are matched to the visit
vector by patient ID and timestamp. Over time, these vectors form a
longitudinal digital twin of the individual. Machine learning models,
trained on the patient's own history, establish a personal normal range
for every parameter. At each subsequent visit, the system compares the
new visit vector against the personal baseline, flagging statistically
significant deviations.

Drug Response Monitoring:

When a physician prescribes a new medication, the visit at which the
prescription is written serves as the baseline. At the follow-up visit,
the platform automatically highlights all parameters that have shifted
beyond the patient's pre-drug variability: posture asymmetries, thermal
changes, vocal tremor, gait alterations, heart rate variability. The
physician sees a concise before-and-after comparison, enabling earlier
detection of adverse effects or lack of efficacy.

Privacy and Security:

All data capture and processing occur within the clinic's existing
HIPAA-compliant infrastructure. Raw sensor streams are processed
on-device into abstracted features; identifiable video and audio are
never stored. The digital twin file is encrypted and owned by the
patient, with access controlled by the same consent framework that
governs medical records.

\-\--

Feasibility

Every individual sensor technology is commercially proven and
mass-produced:

· Load cells and capacitive sensors are standard in industrial scales,
consumer wearables, and automotive seats.

· Pressure mats are used in gait labs and retail analytics.

· RGB and thermal cameras are commodities; thermal resolution adequate
for medical screening (0.1°C) is available in sub-\$500 modules.

· MEMS microphone arrays are deployed in smart speakers and telemedicine
carts.

· Dry-contact EEG/EKG headsets (e.g., Muse, OpenBCI) are sold for
consumer and clinical use.

· VOC sensors (metal-oxide semiconductor) are found in air quality
monitors.

· AR monoculars are detailed in a companion white paper; the optical
path is a simple microdisplay and lens.

· Edge servers with sufficient GPU capacity for real-time multi-sensor
fusion (NVIDIA Jetson AGX Orin or similar) are deployed in autonomous
vehicles and manufacturing.

The integration challenge is software: multi-sensor calibration, feature
extraction, and longitudinal modeling. This is well within the
capabilities of modern medical AI frameworks and existing hospital IT
systems.

\-\--

Challenges

1\. Clinical validation: The platform must demonstrate that its detected
deviations correlate with clinically meaningful outcomes. Prospective
studies are required before it can influence treatment decisions.

2\. Clinician adoption: The AR monocular or tablet interface must be
faster and more intuitive than current practice. A clunky system will be
abandoned. Iterative design with practicing physicians is essential.

3\. Patient acceptance: A room full of sensors may feel intrusive.
Transparent communication, visible consent indicators, and the absence
of body-worn devices (save the optional headband) mitigate this.

4\. Data overload: A high-dimensional visit vector risks overwhelming
the physician with false positives. The system must present only
statistically robust, clinically relevant deviations, prioritized by
severity.

5\. Cost ceiling: Per-room cost must remain below the budget threshold
for broad deployment. Component selection, volume manufacturing, and a
single edge server per clinic (not per room) can achieve a target of a
few thousand dollars per room.

6\. Interoperability: The platform must integrate with existing EHR
systems (Epic, Cerner) and lab information systems. Standards-based APIs
(HL7 FHIR) are the bridge.

7\. Regulatory path: The platform is a diagnostic aid, not a standalone
diagnostic device. FDA 510(k) clearance as a Class II medical device is
the likely path; the software may be treated as a SaMD (Software as a
Medical Device).

\-\--

Development Path

1\. Phase 1 -- Sensor bench validation: Assemble all core sensors on a
test rig. Validate that chair sensors capture heart rate and respiratory
rate against clinical gold standards. Confirm thermal camera accuracy.

2\. Phase 2 -- Simulated exam room: Build a single-room prototype in a
hospital simulation lab. Recruit clinicians to perform mock exams while
the system captures data. Iterate the AR interface based on feedback.

3\. Phase 3 -- Clinical feasibility study: Deploy in a single exam room
in a partner clinic for 6 months, with patient consent. Collect visit
vectors and compare with traditional chart data. Train the
personal-baseline model.

4\. Phase 4 -- Drug monitoring pilot: Partner with a clinical trial site
or a specialty clinic (e.g., rheumatology, neurology) where medication
changes are frequent. Measure the platform's ability to detect known
drug side effects earlier than standard assessment.

5\. Phase 5 -- Regulatory submission and open release: Submit for FDA
510(k) clearance. Simultaneously publish the sensor fusion algorithms,
interface standards, and hardware specifications under a public-domain
framework to ensure interoperability and prevent vendor lock-in.

\-\--

Technology Stack

Component Example Tech

Chair Sensors 4x 50 kg load cells (HX711 ADC), 2x capacitive sensing
arrays (MPR121), under-armrest PCB

Floor Mat Custom pressure-sensing mat (16x16 FSR array) or commercial
gait mat (GAITRite)

RGB Cameras 2x 12 MP global-shutter USB3 cameras (FLIR Blackfly S) with
IR-cut filters

Thermal Camera FLIR Lepton 3.5 or MLX90640, 160x120 resolution, 0.1°C
sensitivity

Microphone Array 4x Knowles SPH0641LM4H-1 MEMS mics, beamforming on XMOS
processor

EEG/EKG Headband OpenBCI Cyton-compatible dry electrodes, 8-channel,
Bluetooth

Breath Sniffer Figaro TGS2600 or Sensirion SGP41 VOC sensor, small
inline fan

AR Monocular 0.23\" OLED microdisplay, aspheric lens, mounted on
lightweight headband (see AR Monocular white paper)

Edge Server NVIDIA Jetson AGX Orin, 64 GB RAM, local RAID storage,
encrypted

Software Custom C++/Python sensor fusion pipeline; PyTorch models for
feature extraction; HL7 FHIR API for EHR integration

Tablet Interface 10\" Android tablet with custom physician data-entry
app, Wi-Fi 6

\-\--

Author Note

This white paper describes a platform for capturing the data that
already flows through every doctor's office---heat, motion, voice,
posture---and turning it into a structured, comparable record. The
Clinical Twin Platform is not a finished product; it is a blueprint for
an exam room that remembers, that notices when something changes, and
that gives the physician a new set of senses without getting in their
way. The monocular makes the invisible visible. The sensors make the
transient permanent. The result is a machine that builds a digital
mirror of every patient, visit by visit, and makes that mirror
clinically useful. The design is public prior art. Build it into every
exam room, and let the data speak.
