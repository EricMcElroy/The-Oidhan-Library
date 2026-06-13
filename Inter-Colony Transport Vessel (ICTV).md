Inter-Colony Transport Vessel (ICTV) --- Tweendecker Retrofit

System ID: 95 (pending)

Status: White paper --- concept and retrofit architecture

Parent Systems: Inter-Colony Logistics Network, Exo Cluster, City
Environmental Sensors (sensor architecture heritage), Dummy Terminals
(display interface heritage)

Overview

A first-generation inter-colony transport vessel built on a retrofitted
4,500 DWT geared tweendecker hull. The base vessel is a proven workhorse
with onboard cranes, adjustable intermediate decks, and the ability to
self-load/unload at undeveloped docks. The retrofit amplifies this
capability with automation, energy efficiency, environmental separation,
and crew reduction, transforming it into a flexible circulatory node for
the simulated deep-space colony network.

Base Platform

· Type: Geared tweendecker, single screw, medium-speed diesel

· DWT: 4,500 metric tons

· Cargo capacity: \~4,000 MT payload, \~6,000 m³ bale capacity

· Cranes: Two deck cranes, estimated 30--40 tonne capacity each (tandem
lift to 60--80 tonnes)

· Fuel burn: \~9.0 MT marine diesel per 24 hours at 11 knots cruise;
\~1.2 MT/day in port during cargo ops

· Crew: 10--12 (pre-retrofit baseline)

Retrofit Systems

Powered Tweendeck Reconfiguration

Replace manually handled pontoon lids with electric screw-jack or
hydraulic panels. Each panel locks/unlocks and repositions itself under
tablet control. Reconfiguration between cargo manifests occurs in
minutes, not hours, and can proceed in parallel with crane operations.
Panel position maps feed the crane operator a live hold layout.

Crane Autonomy Lite

· Stereo cameras and LED illumination inside cargo holds and under
tweendecks

· Hook-mounted IMU for anti-sway compensation tied to ship\'s central
IMU (roll/pitch/heave)

· Predictive load path overlay on operator tablet

· Remote operation capability --- operator can stand at optimal vantage
point

· Reduces required deck crew by 1--2 personnel; eliminates need for a
spotter in the hold

Automated Ballast Trim

· Motorized gate valves on ballast tanks replace manual pneumatic
controls

· Central controller reads vessel inclination and crane load cell data

· Maintains deck within 1° of level during cargo ops without crew
intervention

· Cuts port turnaround time; eliminates ballast-related crane pauses

Environmental Separation (Biologicals Bay)

· One tweendeck bay (approximately 500 m³) fitted with independent
climate control: temperature ±0.5°C, humidity ±3%

· Removable insulated bulkheads; connects to ship\'s electrical bus with
priority

· Used for seeds, cultures, pharma intermediates, algae paste, and other
temperature-sensitive cargo

· Bay can be sanitized between cargo types via UV and vapor H₂O₂ cycle

Integrated Fluid Transport

· Dedicated ISO tank container stations with ship-side plumbing for
clean-in-place

· Common tank commodities: bio-oil (Marshalls), ammonia (UAE), algae
slurry, waste cooking oil for recycling

· Reduces container deadheading; fluid cargo can be pumped directly to
colony storage at destination

Energy Management

· Hull efficiency: Silicone foul-release coating + regular in-water
drone cleaning; estimated 5--10% fuel savings

· Propeller upgrade: Kappel tip or boss cap fin retrofit for 3--5%
additional gain

· Hotel load solar/battery: Photovoltaic array on accommodation block
and mast; 100 kWh LiFePO₄ battery bank. Supports 12-hour generator-off
periods at anchor. Eliminates diesel burn for hotel load during daylight
port stays.

· Shore power universal interface: Auto-detecting transformer and cable
reel that accepts 380--480V, 50/60 Hz, with battery bridging during grid
transitions

Navigation & Communication Stack

· Open-source ECDIS on ruggedized dual displays

· AIS, radar overlay, thermal camera for night approaches and debris
detection

· Starlink terminal for real-time weather routing, remote diagnostics,
and demand-signal updates

· Long-range weather-optimized routing that trades transit time against
fuel burn based on cargo urgency

Crew Reduction & Mobile Training

· Engine room monitoring via vibration-powered wireless sensors (ESP32
architecture)

· Thermal cameras and automated watch-round logging reduce unaccompanied
engine room checks

· Target crew: 6--7 (down from 10--12), compliant with flag-state
minimum safe manning

· Freed accommodation space converted to a small workshop/training room
with Exo Cluster compute, 3D printer, and workbench

· Crew not on watch are cross-training or fabricating repair parts;
vessel functions as a mobile university between ports

Cargo Handling for Undeveloped Docks

· Ship carries containerized shore modules on first deployment: mobile
crane platform, roll-off ramp, temporary hardstand

· Delivers its own unloading infrastructure to ports that lack it

· QR-coded cargo bays link to manifest; shore crew with a phone scan
knows exactly where each item goes

Implementation Phases

1\. Phase 1 --- Base Vessel Acquisition: Procure used 4,500 DWT
tweendecker hull in sound condition. Dry dock for hull survey, coating,
and propeller retrofit.

2\. Phase 2 --- Mechanical Retrofit: Install powered tweendeck panels,
motorized ballast valves, cargo bay cameras, climate-controlled bay.
Install solar array and battery bank.

3\. Phase 3 --- Compute & Automation: Crane autonomy kit, central IMU,
ballast controller, navigation stack, Starlink, engine room wireless
sensors.

4\. Phase 4 --- Network Integration: Demand-signal routing software,
digital twin connection, crew training syllabus, first triangular loop
with backhaul planning.

Cost Targets

· Base vessel (used, good condition): \$4.0--4.5M

· Retrofit package (all systems): estimated \$1.2--2.0M depending on
engine condition and crane upgrades

· Total: \~\$6M for a vessel that outperforms newbuild equivalents in
the \$15--20M range on the specific inter-colony mission profile

Relationship to Other Systems

· Exo Cluster: Compute backbone for crane autonomy, ballast control, and
navigation

· City Environmental Sensors: ESP32 sensor architecture adapted for
engine room monitoring and cargo bay environmental logging

· Dummy Terminals: Ruggedized tablet interfaces for crane operation,
ballast control, and cargo manifest management

· Hollywood Killer (pharma branch): Destination for Malta\'s pharma
intermediate cargo; provides trial recruitment and data compensation for
colony medical research

· Agora System: Legal and cooperative ownership framework for the vessel
and the logistics network
