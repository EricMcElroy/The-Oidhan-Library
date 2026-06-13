KEYED INTERLOCK BUS (KIB)

A scalable, shape-coded, hot-swappable power and data interconnect
standard for wearables, electronics, vehicles, and robotics.

Author: Eric Don McElroy

Date: 2026-06-08

Contact: eric.mcelroy@gmail.com, https://substack.com/@eskamick

Version: 1.0

Status: Public Release / Prior Art Disclosure

\-\--

Abstract

The Keyed Interlock Bus is a universal physical connector and protocol
standard that uses a distinct mechanical key shape to ensure foolproof,
hot-swappable attachment of batteries, sensors, body panels, and
peripheral modules. Identical in concept to an appliance cord that plugs
into the grid, the KIB provides every device with a male base port that
supplies power, data, and a small backup energy reserve. Female
modules---ranging from smartwatch battery discs to vehicle motor
controllers---snap into place via a guided, self-aligning key geometry.
The standard scales across multiple size classes without altering the
core key profile, enabling a common ecosystem from wrist‑worn wearables
to full‑scale electric vehicles.

\-\--

Problem

Modular electronics and electric vehicles lack a single interconnection
philosophy that spans device sizes. USB‑C handles data and power but is
not mechanically suited for high‑current vehicle batteries, tool‑free
body panel swaps, or quick‑release wearable modules. Industrial
connectors are robust but not designed for end‑user hot‑swapping or
aesthetic integration. The result is a fragmented landscape where every
product line reinvents the wheel, batteries are hard‑wired or require
tools to change, and consumers cannot share modules across devices. A
unified, physically obvious, scalable "plug‑and‑play" interface is
missing.

\-\--

Concept

The Keyed Interlock Bus defines a male‑host / female‑module docking
standard. Every host device---a watch strap, a tabletop scanner, a golf
cart chassis, a robot core---incorporates a male port with a unique,
semi‑circular key shape featuring tapered, non‑parallel sidewalls. The
female connector, built into any swappable module (battery disc, sensor
pack, body panel, cup holder), slides over the male port and clicks into
place with a positive mechanical lock. The key shape eliminates
misalignment: a half‑circle with angled flats forces correct orientation
without the user having to visually inspect.

Small‑scale implementations (wearables) pack a tiny battery directly
inside the female connector itself. For instance, a smartwatch strap
ends in a male KIB port. The user clicks on a disc‑shaped battery that
includes the female connector and a small cell. The same disc can be
magnetically attached to a chest plate, pendant necklace, or clip using
an adapter that also carries a KIB male port. When the disc is removed,
the host device runs momentarily off an onboard capacitor or
micro‑battery to allow a hot swap without shutting down.

Mid‑scale (home scanners, small electronics) use the same key geometry
at a larger physical size, carrying more power and data lines. Swappable
sensor packs, additional processing modules, or external battery packs
all mate via the identical mechanical interface.

Vehicle class (mopeds, golf carts, robots) scales the connector further.
The same key shape, now capable of handling tens to hundreds of amps and
a CAN‑bus network, forms the backbone of the hot‑swappable ecosystem
described in the Super Moped and Super Golf Cart papers. Body panels,
motors, and battery packs slide and lock into place with the same
intuitive motion as a smaller module.

Universal ID. Every module identifies itself over the data bus upon
connection (presence‑detect pin + digital handshake). The host adjusts
power delivery and communication protocols accordingly. The bus carries
power, ground, CAN bus (vehicle class) or I²C/SPI (smaller classes), and
a backup power rail that keeps the host alive during swaps.

\-\--

Feasibility

The KIB is a mechanical and electrical wrapper around existing connector
technology, requiring no fundamental invention.

· Key shape. Molded polymer shells with custom‑keyed interiors can be
rapidly prototyped with 3D printing and eventually injection‑molded. The
non‑parallel wall taper is a standard design‑for‑assembly feature seen
in blind‑mate connectors (e.g., Molex Mini‑Fit, Anderson Powerpole).

· Power and data contacts. Off‑the‑shelf spring‑loaded pogo pins
(Mill‑Max, Preci‑Dip) for low‑current wearables, and solid
amphenol‑style blade contacts for high‑current vehicle classes. CAN
transceivers (MCP2551, TJA1050) are ubiquitous and cost under \$1.

· Small‑scale battery‑in‑connector. Commercially available
lithium‑polymer pouch cells (e.g., 3.7 V 100 mAh) can be integrated into
a female connector housing, with a dedicated charging line separate from
the bus. Similar architectures exist in rechargeable hearing aids and
wireless earbud cases.

· Magnetic backing. The chest‑plate and pendant adapters use standard
neodymium magnets (N52) with the KIB male port centered. The magnetic
force doubles as physical retention, augmented by a mechanical key for
positive alignment.

· Scaling proof. Industrial circular connectors (LEMO, Fischer) are
produced in multiple shell sizes with identical pin configurations.
USB‑C, despite its small size, supports up to 240 W and high‑speed data.
The KIB simply adopts a custom key shape that remains constant across
all size classes, using larger bodies for more power without redesigning
the alignment feature.

The largest connectors can be built using modular inserts (Phoenix
Contact heavy‑duty connectors) inside a custom KIB‑shaped housing.

\-\--

Challenges

· Mechanical wear. Hot‑swapping many times per day (watches, batteries)
demands pogo pins or contacts rated for 10,000+ cycles. Gold‑plated,
high‑cycle pogo pins exist but increase cost.

· Environmental sealing. Vehicle‑class connectors must resist mud,
water, and vibration. IP67‑rated gaskets and locking rings add
complexity to the simple slide‑on motion.

· Standard adoption. The value of KIB is in its ubiquity; achieving
industry buy‑in requires an open, royalty‑free specification and
early‑stage cross‑licensing with hardware manufacturers.

· Backward compatibility with existing USB/Lightning. Not a direct
threat, but KIB is designed as a system interconnect, not a peripheral
cable; it complements rather than replaces existing external data ports.

\-\--

Development Path

1\. Define key profile and pinout. Engineer the exact semi‑circle
geometry with angled walls (e.g., 5° taper) and a locating notch.
Designate pin assignments for power, ground, presence detect, and data
lines for each size class.

2\. Prototype three size classes:

· Micro (25 mm wide) for wearables, with integrated 150 mAh cell.

· Mini (50 mm) for tabletop/portable electronics.

· Standard (100 mm) for vehicle/robotics.

3\. Produce reference host devices. A wrist strap, a chest‑plate
adapter, a pendant, a small desktop scanner, and a dummy vehicle
chassis. Validate hot‑swap and data handshake.

4\. Draft open standard document. Publish mechanical CAD (STEP), pinout
table, communication protocol (CANopen‑lite or simple I²C ID string),
and licensing statement (public domain).

5\. Compliance testing. Cycle connectors to failure, measure voltage
drop under load, IP‑certify the vehicle class.

6\. Ecosystem seeding. Open‑source PCB footprints, 3D‑printable
housings, and a sample driver library for Arduino/STM32.

\-\--

Technology Stack

· Contacts (Micro): Mill‑Max 0906‑9 gold pogo pins, 2.5 A rated,
dual‑spring.

· Contacts (Standard): Anderson Powerpole PP15/45 contacts inside a
keyed housing, or Amphenol SurLok Plus for high current.

· Data bus (Micro/Mini): I²C (3.3 V), with device ID EEPROM in module
(Microchip 24AA02E48).

· Data bus (Standard): CAN 2.0B, MCP2551 transceiver, 1 Mbps.

· Presence detect: Pull‑low pin with 10 kΩ pull‑up on host; module
grounds the pin upon full insertion.

· Battery (micro connector): 3.7 V 150 mAh Li‑polymer pouch cell (402025
size) with integrated TP4056 charge controller on the host side.

· Host backup power: 0.5 F supercapacitor or small 20 mAh Li‑poly
onboard to maintain device operation during hot‑swap.

· Key housing: SLS‑printed PA12 or injection‑molded ABS/PC blend;
magnets N52 disc 8×3 mm for wearable adapters.

· Driver library: Arduino CAN‑bus and I²C examples; STM32 HAL reference
firmware.

\-\--

Author Note

This white paper is a public‑domain prior art disclosure, intended to
prevent patent encumbrance of the described keyed bus connector system
and its scaling methodology. The KIB geometry, hot‑swap protocol, and
battery‑in‑connector variant are placed into the public domain.
Builders, manufacturers, and open‑source hardware communities are free
to implement, modify, and integrate the system without restriction. For
technical diagrams or collaboration, contact the author at the addresses
above.
