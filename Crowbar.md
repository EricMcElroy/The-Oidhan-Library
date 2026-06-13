CROWBAR

A local‑only CAN bus monitor and limited injector for non‑safety vehicle
features

Author: Eric Don McElroy

Date: 2026-06-09

Contact: eric.mcelroy@gmail.com, https://substack.com/@eskamick

Version: 1.0

Status: Public Release / Prior Art Disclosure

\-\--

Abstract

Crowbar is a low‑cost, open hardware device built around an ESP32
microcontroller and a CAN bus transceiver. It taps into a vehicle's
Controller Area Network (CAN) via the OBD‑II port or direct wired
connection, providing read‑only monitoring by default. With explicit
user action (physical switch or local wireless command), Crowbar can
inject pre‑researched CAN frames to correct non‑safety feature
faults---for example, re‑enabling heated seats after a payment
authorization error. The device operates only over short‑range Wi‑Fi or
BLE (\~5 ft), has no cloud connectivity, and includes a safety guard
that prevents injection onto brakes, steering, airbags, or throttle. All
design and firmware are released as prior art to remain unencumbered.

\-\--

Problem

Modern vehicles use CAN bus to communicate between electronic control
units (ECUs). When a legitimate user experiences a software fault---such
as a failed authorization handshake for a paid convenience feature
(heated seats, ambient lighting, mirror positioning)---there is no
standard, user‑owned tool to locally correct the issue. Owners are
forced to visit dealerships, replace ECUs, or accept lost functionality.
Existing aftermarket CAN tools are either read‑only, prohibitively
expensive, or lack safety boundaries, risking accidental interference
with critical systems.

\-\--

Concept

Crowbar is a handheld or inline device that:

· Connects to the vehicle's CAN bus (high and low lines) via an OBD‑II
pigtail or soldered taps.

· Uses an ESP32 with integrated Wi‑Fi and BLE for local wireless access.

· Monitors all CAN traffic and logs packets to a connected phone/laptop
or onboard flash.

· Injects CAN frames only when a physical safety switch is engaged and a
deliberate command is sent (e.g., a single BLE packet or button press).

· Ships with a whitelist of allowed CAN IDs for injection---confined to
infotainment, comfort, and lighting domains.

· Comes with open documentation for users to research and construct
corrective packets for their specific vehicle and fault.

Example use case: After paying a subscription for heated seats, the seat
module fails to receive the "authorized" flag. The user looks up the
correct CAN ID and data payload online, uses Crowbar's injection mode to
send that frame once, and the seats resume normal operation.

\-\--

Feasibility

All components are commercially available, low‑cost, and
well‑documented.

Hardware (per‑unit cost estimate, single quantities)

Component Example Part Cost (USD)

ESP32 development board (Wi‑Fi/BLE) ESP32‑DevKitC or ESP32‑S3‑Mini
\$6--\$10

CAN controller + transceiver module MCP2515 + TJA1050 module \$3--\$5

OBD‑II male pigtail (bare wires) J1962M pigtail \$5--\$8

Safety toggle switch (physical injection enable) SPDT mini switch
\$1--\$2

Voltage regulator (12V to 5V) LM2596 module (if not on ESP32 board)
\$2--\$3

Enclosure (optional) 3D‑printed or ABS box \$2--\$5

Total DIY build \$19--\$33

Pre‑assembled (small batch) including assembly and programming
\~\$45--\$60

Analogous Systems

· CANtact (open source CAN interface) -- similar hardware but lacks
safety‑limited injection and local wireless.

· Macchina M2 (automotive diagnostics) -- more powerful but higher cost
(\~\$150+).

· ESP32‑CAN‑OBD‑II dongles sold on AliExpress -- exist but typically no
safety guard and often closed source.

Crowbar differentiates by: explicit physical injection guard,
whitelist‑only domains, prior art disclosure, and sub‑\$35 DIY cost.

Power

Powered from vehicle 12V (OBD‑II pin 16) via a buck converter to 5V.
Current draw: \~70 mA (monitoring) to \~200 mA (injecting + Wi‑Fi
active).

\-\--

Challenges

1\. CAN bus termination -- The device must not add extra termination.
Solution: use high‑impedance listening and passive tap; transceiver
module handles bus loading correctly.

2\. Bit timing mismatch -- Different vehicles use different CAN bit
rates (125 kbps, 250 kbps, 500 kbps). Solution: auto‑baud detection or
user‑configurable setting via web interface.

3\. Packet injection safety -- No system is 100% failsafe. Mitigations:
hardware injection enable switch, firmware whitelist of allowed CAN IDs,
and a strict 10‑packet‑per‑second limit on injection.

4\. Legal / warranty concerns -- User assumes all risk. White paper
includes clear warning that injection may void warranties or violate
local regulations if used improperly.

5\. Reverse‑engineering effort -- Users must research correct CAN IDs
for their vehicle. The project will host a community wiki for shared
packet databases.

\-\--

Development Path

Phase Milestone Estimated Effort

1 Prototype on breadboard: ESP32 + MCP2515, read CAN traffic 2 weeks

2 Add safety switch and injection test on bench (simulated CAN bus) 1
week

3 Implement Wi‑Fi web dashboard for monitoring and packet crafting 2
weeks

4 Vehicle testing on non‑critical bus (e.g., infotainment CAN) 2 weeks

5 Whitelist generation for 10 common vehicle models 4 weeks (community)

6 Release open hardware design (KiCad), firmware (Arduino/ESP‑IDF), and
documentation ongoing

\-\--

Technology Stack

· Microcontroller: ESP32 (any variant with CAN controller, e.g.,
ESP32‑WROOM‑32, ESP32‑S3)

· CAN controller: Internal ESP32's TWAI controller (for native CAN) or
external MCP2515 via SPI

· CAN transceiver: TJA1050, SN65HVD230, or MCP2551

· Firmware language: C++ (Arduino framework) or Rust (esp‑hal)

· Wireless: ESP32 native Wi‑Fi (802.11 b/g/n) and BLE 4.2

· User interface: Web server (HTTP + WebSockets) or BLE GATT custom
service

· Safety logic: GPIO‑read of physical switch + in‑memory whitelist array

· Power: LM2596 (12V→5V) or automotive‑grade DC‑DC (e.g., Traco Power
TSR 1‑2450)

\-\--

Author Note

This document serves as prior art disclosure and public domain
reference. The Crowbar design, including schematics, bill of materials,
and firmware architecture, is intended to remain open and unencumbered.
No patent, copyright, or trade secret is claimed. Builders, makers, and
automotive hobbyists are encouraged to implement, improve, and
distribute Crowbar freely. Attribution to Eric Don McElroy is
appreciated but not required. The goal is a safe, affordable, user‑owned
tool for correcting software faults in non‑safety vehicle features.
Implement responsibly.

---

The landscape for \"Right to Repair\" has shifted dramatically in the
last two years. Here's an update for your write-up, directly connecting
the latest regulations to the Crowbar concept.

⚖️ The Federal Push: The REPAIR Act & The House Bill

At the federal level, the conversation has moved from abstract debates
to actual legislative text. The primary federal bill is the REPAIR Act
(H.R. 1566 / S. 1379), which stands for \"Right to Equitable and
Professional Auto Industry Repair\".

· Purpose: It mandates that manufacturers provide vehicle owners and
independent repair shops with the same access to diagnostic tools,
software, and data as they do for their franchised dealerships.

· Current Status: The bill was introduced in the House in February 2025
and has already been advanced by the House Energy and Commerce
Subcommittee, indicating significant bipartisan support.

· Embedded in Larger Legislation: A version of its provisions has also
been incorporated into the Motor Vehicle Modernization Act of 2026 (H.R.
7389) , which passed the House Energy and Commerce Committee by a 48-1
vote earlier this month, suggesting the \"Right to Repair\" concept is
being treated as a critical component of future automotive standards.

🏛️ The State Battlegrounds: Successes & Stalls

While federal legislation moves forward, state-level fights are creating
a complex patchwork of laws.

· Massachusetts is the Battleground: Voters overwhelmingly approved a
law granting independent shops access to \"telematics\" (wireless
vehicle data). After a long legal fight by automakers, a federal judge
denied their challenge to block the law in early 2025, calling security
claims insufficient. The industry has appealed, but for now, it remains
the most expansive state law on the books.

· Other States are Moving: Maine and Wisconsin are on parallel tracks
with legislation similar to Massachusetts' framework, though with
ongoing political delays. Notably, Connecticut and Oklahoma enacted new
R2R protections in May 2026, with more than a dozen states now having
some form of ADAS calibration or repair access standards.

🇪🇺 The International Landscape: The EU Data Act

It\'s also worth noting that the EU\'s general Data Act came into full
force in September 2025. It establishes a fundamental right for users of
connected devices (including cars) to access and share the data those
devices generate with third parties of their choice. While not a
car-specific law, it forces manufacturers to offer \"fair and
transparent\" access to vehicle data.

🏭 The Industry\'s Response (Not All Opposition)

Interestingly, the narrative isn\'t strictly \"US vs. automakers.\"

· Some Support: Groups like the Commercial Vehicle Solutions Network
(CVSN) are actively lobbying for the REPAIR Act, showing the commercial
vehicle aftermarket sees it as vital to their survival.

· Industry Opposition Persists: The primary opposition remains the
dealer associations, who argue these laws present safety and
cybersecurity risks.

🔗 How This Applies to Crowbar

This evolving legal landscape is critical to the Crowbar\'s viability
and legitimacy:

· Legal Shield: The right to repair laws are becoming the explicit legal
justification for devices like Crowbar to exist. They are enshrining the
right of an owner to \"tap in\" and diagnose issues.

· Anti-DRM Measures: It directly combats the practice of \"DRM for
cars,\" where software locks prevent repairs or modifications.

· Potential Obstacle: The biggest long-term threat is the adoption of
encrypted CAN protocols by manufacturers, which could physically prevent
a simple device from injecting packets, even if you legally own the car.
The ultimate goal of these laws is to force manufacturers to provide
authorized decryption keys to owners, ensuring actual access, not just
theoretical access.

📜 Good Explanation & Resource

For a deeper, neutral background, the Wikipedia article \"Right to
repair\" provides a fantastic historical overview of the movement and
its legal origins. It covers the key differences between general
consumer electronics and the unique automotive regulatory battles.

Do you want to dive deeper into any of these aspects, or shall we
finalize these notes?
