Addendum B: Multi‑Vector Friction Shaping -- Chemicals, Fields, Time,
and Media

B.1 Why Only Two Metals?

The base CFP process uses rod (metal A) and master (metal B or ceramic).
But the interface is a chemical reactor running at 500--1000°C, 10--100
MPa contact pressure, and 1--50 m/s sliding velocity. That environment
can activate additional reactants.

Introduce a third chemical as:

· Paste applied to master before contact.

· Vapor injected into the gap (nitrogen already there -- add oxygen,
methane, or metal halides).

· Liquid bath (submerged operation -- Section B.6).

Reactions possible:

· Carburizing: Add methane → carbon diffuses into molten metal surface →
hard steel mirror (wear‑resistant).

· Nitriding: Add ammonia or nitrogen plasma → surface nitrides (hard,
corrosion‑resistant).

· Oxidation: Add water vapor or oxygen → controlled oxide layer (colored
mirrors, passivation).

· Metal infiltration: Add copper paste between aluminum rod and steel
master → in‑situ brazing, then shear off → composite mirror.

Result: The mirror surface is not just shaped -- it is alloyed or coated
during the same friction pass. No secondary coating step.

\-\--

B.2 Multiple Shaping Fields

The master is not the only shaping tool. Add:

B.2.1 Magnetic Field (DC or Pulsed)

· Place an electromagnet around the rod end, coaxial.

· Field strength 0.1--1 T.

· Effect on molten layer: Lorentz force induces azimuthal flow
(stirring), homogenizing temperature and composition. Also pinches the
molten layer against the master (extra pressure) without mechanical
force.

B.2.2 Induction Heating (Additional Heat Vector)

· Add an induction coil (off‑the‑shelf, 1--10 kW, 50--200 kHz) around
the rod, just behind the contact zone.

· Purpose: Pre‑heat the rod to just below melting before friction
contact. Then friction only needs to add the last ΔT. Reduces mechanical
wear on master, allows harder materials (steel rod with steel master --
normally welds).

B.2.3 Physical Interposition -- Dynamic Shaping Tool

· A third moving element: a secondary rod or blade that pushes into the
molten layer from the side during spinning.

· Controlled by a linear actuator.

· Effect: Creates non‑axisymmetric shapes -- elliptical mirrors,
off‑axis parabolas, or even faceted surfaces. The spinning rod provides
the base axisymmetry; the interposer breaks it at specific angles.

B.2.4 Ultrasonic Vibration (20--100 kHz)

· Bolt a piezoelectric transducer to the master holder.

· Effect: Cavitation in the molten layer (if any) + reduced friction
coefficient (sonic lubrication). Smoother surface finish, less heat
generation, allows slower speeds.

Vector stacking: Run magnetic field + induction heat + ultrasonic +
mechanical master simultaneously. Each vector subtracts from the burden
on the others. The machine becomes a multi‑field friction cell, not just
a polisher.

\-\--

B.3 Time as a Vector -- Speed & Dwell

The base process assumes fast contact (0.1--1 sec) and fast retract.
Vary:

B.3.1 Slower Contact (0.1--0.01 m/s approach, not m/s)

· Dwell time 5--30 seconds.

· Effect: The molten layer grows thicker (microns → tens of microns). If
thicker than the Bond number threshold, centrifugal forces will create a
paraboloid. That is desirable if you want a concave mirror without a
concave master. Control dwell time to dial in curvature: short dwell =
flat, long dwell = curved.

B.3.2 Faster Spin (100,000+ RPM)

· Use air turbine spindle (dental drill, 300,000 RPM possible).

· Effect: Centrifugal ejection of debris becomes the dominant material
removal mechanism. The rod end loses material faster than it can melt
and flow. This is friction machining -- subtractive only. Useful for
rough shaping before polishing passes.

B.3.3 Pulsed Contact (On‑Off at kHz rates)

· Piezoelectric actuator to vibrate the master axially at 1--10 kHz with
small amplitude (1--10 µm).

· Effect: The molten layer experiences alternating compression and
tension. Tension phase pulls molten metal into micro‑cavities (fills
pores). Compression phase squeezes out excess. Results in dense,
void‑free surface -- critical for reflective coatings.

B.3.4 Time Sequencing -- The Recipe

Each mirror gets a time recipe:

1\. Fast spin (60k RPM), no contact -- centrifugal smoothing
(pre‑shape).

2\. Slow approach (0.01 m/s), dwell 2 sec -- paraboloid formation.

3\. Ultrasonic pulse while cooling -- stress relief.

4\. Induction heat + magnetic field while retracting -- homogenize
alloy.

Time is a vector you program, not just a parameter.

\-\--

B.4 Chemical Environment -- Beyond Air

The gap is currently nitrogen (inert). Change the fluid:

B.4.1 Liquid Submersion (Full Bath)

· Place the entire rod end and master inside a tank of dielectric fluid
(PAO -- same as Tesla Matrix). Or water. Or molten salt.

· Advantages:

· Quenching is instant (no separate nitrogen jet).

· No debris dust -- all particles trapped in liquid.

· Liquid provides hydrostatic pressure (prevents cavitation voids).

· Can add reactive chemicals (e.g., boric acid in water → boronizes
surface).

B.4.2 Water (Chemically Active)

· Distilled water as coolant/quench, but also reactant.

· At friction temperatures, water dissociates into H₂ and O₂. Oxygen
oxidizes metal (controlled rust). Hydrogen diffuses into metal (hydrogen
embrittlement -- normally bad, but can be used to create brittle surface
layers that later spall off, leaving a textured finish).

B.4.3 Void (Vacuum)

· Seal the chamber, evacuate to 10⁻² torr (cheap rotary vane pump).

· Effect: No oxidation. No gas bubbles in molten layer. No convective
heat loss -- the molten layer stays molten longer, allowing slower
retract and more flow. Also eliminates any air bearing effect -- the rod
and master contact fully, increasing friction efficiency.

B.4.4 Reactive Liquid -- Electrolytic Friction

· Submerge in dilute sulfuric acid (10% H₂SO₄). Apply DC voltage between
rod (anode) and master (cathode).

· Effect: Friction removes passive oxide layer, exposing fresh metal.
Electrochemical dissolution (anodic etching) shapes the surface without
mechanical contact. The master only serves as electrical contact and
mild abrasive. This is electrochemical machining (ECM) plus friction --
extremely high material removal, no tool wear.

Vector stacking: Acid bath + ultrasonic + magnetic field + spinning rod
= ultra‑fast shaping of hard metals (stainless, titanium) that normally
weld to masters.

\-\--

B.5 What Happens When You Do All of This at Once?

The machine is no longer a mirror maker. It is a universal
friction‑field reactor capable of:

· Alloying (introduce third element via paste or vapor).

· Texturing (ultrasonic + pulsed contact = micro‑patterns).

· Coating (reactive liquid deposits compound layers).

· Machining (vacuum + high speed = ablation only).

· Polishing (slow, inert, low force).

· Heat treating (induction + quench bath = surface hardening).

All in the same workcell. Off‑the‑shelf parts, because every added
vector is a standard industrial component: electromagnet, induction
heater, ultrasonic transducer, vacuum pump, acid bath, etc.

\-\--

B.6 The Cascade -- Example Recipe for a Titanium Concave Mirror
(normally impossible by friction because Ti welds)

1\. Setup: Rod = Ti‑6Al‑4V. Master = tungsten carbide (concave). Bath =
10% H₂SO₄ + 5% HF (etchant). Apply 5V DC (rod +, master --). Vacuum 10⁻¹
torr.

2\. First pass: Spinning rod at 20k RPM, no contact, only
electrochemical etching (field shaping). Surface roughened.

3\. Second pass: Add contact with low force (10 N). Friction + etching +
magnetic field (0.5 T) stirs the etched layer. Material removal rate 10×
higher than dry friction.

4\. Third pass: Turn off voltage, fill bath with PAO (rinse), add
induction heat (preheat rod to 800°C). Friction contact with nitrogen
purge. Molten layer forms without welding (oxide prevented by
vacuum+PAO).

5\. Cool: Remove bath, spray with water (flash steam clean). Result:
titanium mirror, concave, polished, no welding.

Each vector enables a material or shape that was impossible with
friction alone.

\-\--

B.7 Conclusion -- The Machine as a Vector Space

The original CFP paper described a 2‑vector system (mechanical force +
rotational speed). This addendum expands to:

· Chemical vectors (reactive gases, liquids, pastes).

· Field vectors (magnetic, electric, ultrasonic).

· Thermal vectors (induction, bath temperature).

· Temporal vectors (dwell time, pulse rate, sequence).

· Environmental vectors (vacuum, liquid, air).

Each vector interacts. The machine is not a fixed process -- it is a
programmable friction state where you dial in coordinates in vector
space. The output (mirror flatness, curvature, alloy composition,
coating thickness) is a function of that vector coordinate.

This addendum is released to the public domain. Build the vector
machine.
