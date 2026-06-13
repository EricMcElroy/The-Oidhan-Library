White Paper: Integrated Vending Operating System (IVOS)

A Low‑Cost, Retrofit Platform for Cashless Vending, Inventory
Intelligence, and Passive Revenue

Version 2.1 -- Grounded Edition

Author: Independent Concept Development

Date: June 2026

\-\--

1\. Abstract

The Integrated Vending Operating System (IVOS) is an ESP32‑based
retrofit platform that transforms standard vending machines into
connected, self‑monitoring retail endpoints. By augmenting the machine's
existing coin mechanism and MDB (Multi‑Drop Bus) with a QR‑code payment
gateway, NFC tap‑to‑pay, a full‑colour interactive touchscreen, and a
suite of low‑cost sensors, IVOS enables cashless transactions, dynamic
pricing, real‑time inventory tracking, predictive maintenance, and
digital advertising---all at a hardware cost of under \$100 per machine.
The system can be self‑installed in under an hour per unit, works in
parallel with the original payment mechanisms, and operates offline when
connectivity is lost. This paper presents a complete, grounded bill of
materials with real‑world sourcing, step‑by‑step machine interface
instructions, dedicated human‑centred workflows for consumers, route
drivers, and owners, and a rigorous financial comparison against
traditional vending payment systems. The result is a platform that pays
for itself in weeks, delivers ongoing operating savings, and turns a
static vending machine into a dynamic, high‑margin, data‑driven retail
asset.

\-\--

2\. System Overview

A single IVOS unit consists of:

· ESP32‑S3 microcontroller (Wi‑Fi + Bluetooth) -- the central processor.

· 5‑inch TFT LCD with capacitive touch -- replaces the product selection
panel, displays QR codes, ads, and product information.

· PN532 NFC reader -- for contactless cards, phones, and reusable
customer tokens.

· MDB adapter board -- translates the vending machine's MDB protocol to
UART, enabling the ESP32 to authorise vends and read machine status.

· Sensor suite -- vibration, current, temperature, door switch, and a
PIR motion sensor for proximity wake.

· Physical help button -- vandal‑resistant, for customer assistance.

· 5V power supply module -- tapped from the machine's internal AC
supply.

The cloud backend (a low‑cost VPS or serverless environment) manages
payment processing (Stripe), inventory records, advertising content, and
the owner/driver dashboards. The system can be deployed
incrementally---starting with cashless payment and basic telemetry, then
layering on inventory sensors, advertising, and AI analytics.

\-\--

3\. Complete Bill of Materials (Per Machine)

All prices are per‑unit in small‑lot quantities from common online
sources (Amazon, AliExpress, Adafruit, Mouser). Bulk purchasing can
reduce costs 20‑40%.

Component Suggested Model / Search Term Qty Unit Cost Total

Microcontroller ESP32‑S3 DevKitC‑1 (Wi‑Fi, BLE, 16MB Flash) 1 \$5.00
\$5.00

Display 5″ TFT LCD 800×480 with capacitive touch (SPI) 1 \$18.00 \$18.00

MDB interface board Commercial MDB‑UART adapter (e.g., from NAYAX, or
custom PCB with MDB level‑shifter & CP2102) 1 \$30.00 \$30.00

NFC reader PN532 NFC/RFID module (SPI) 1 \$8.00 \$8.00

Relay module 1‑ch 5V relay module (for legacy machines without MDB,
optional) 1 \$3.00 \$3.00

Vibration/tilt sensor SW‑420 vibration module (digital) 1 \$1.50 \$1.50

Current clamp SCT‑013‑000 split‑core CT (monitors compressor) 1 \$8.00
\$8.00

Temperature sensor DS18B20 waterproof probe (for refrigerated machines)
1 \$3.00 \$3.00

Door switch MC‑38 magnetic reed switch 1 \$1.00 \$1.00

PIR motion sensor AM312 mini PIR module 1 \$2.00 \$2.00

Help button 16mm vandal‑resistant metal push button (momentary, IP65) 1
\$3.00 \$3.00

Power supply Hi‑Link HLK‑PM01 AC‑DC 5V 0.6A step‑down module 1 \$5.00
\$5.00

Wiring & connectors Dupont wires, terminals, heat‑shrink -- \$5.00
\$5.00

Total per machine \$92.50

Optional add‑ons:

· Per‑coil weight sensors (load cell + HX711 board): \~\$3 per coil, for
real‑time inventory.

· External ambient light sensor (BH1750): \$1, for auto screen
brightness.

· Microphone module (MAX9814): \$2, for voice feedback and tamper
detection.

· 3G/4G cellular module (SIM800L): \$8, for locations without Wi‑Fi.

For a typical route of 10 machines, the total hardware investment is
approximately \$925.

\-\--

4\. Machine Interface: How IVOS Talks to Any Vending Machine

Vending machines use the Multi‑Drop Bus (MDB) protocol for communication
between the main controller (VMC) and peripherals (coin changer, bill
validator, cashless device). IVOS impersonates a cashless device on the
MDB bus, allowing it to authorise transactions without modifying the
machine's core logic.

4.1 MDB‑Ready Machines (Post‑2010, e.g., Dixie Narco, Vendo, Royal,
Crane, Wittern)

· Connect the MDB adapter board to the machine's 6‑pin MDB connector.

· The adapter converts the 9‑bit MDB serial protocol to standard UART
(TX/RX) for the ESP32.

· IVOS registers as device type 0x10 (Cashless Device #1). When a
customer selects a product, the VMC sends a Vend Request to IVOS. If a
valid payment token exists (from QR code or NFC), IVOS responds with
Vend Approved. The VMC then vends the product and sends a Vend Success
confirmation.

· IVOS can also read machine state: sold‑out signals, exact change
status, door open, etc.

4.2 Legacy Electromechanical Machines (No MDB)

For older machines, IVOS can directly control the dispensing motors via
relays and optocouplers, simulating the button matrix and monitoring
motor feedback. This is more wiring‑intensive but still feasible. In
such cases, the original coin acceptor remains in parallel; IVOS simply
"presses" the same button via a relay when a valid payment is received.

4.3 Dual‑Mode & Fail‑Safe Operation

All connections are in parallel. Cash and coins still work exactly as
before. If the ESP32 fails or loses power, the machine continues to
operate normally as a standard coin‑operated unit. This eliminates the
risk of total machine downtime due to a retrofit failure.

\-\--

5\. Human‑Machine Interface (HMI)

IVOS treats three distinct human roles---consumer, route
driver/restocker, and owner---as integral subsystems, each with a
dedicated interface.

5.1 Consumer Interface

At the machine (LCD touchscreen):

· Idle mode: Rotating product carousel with high‑quality images, prices,
and a persistent QR code. "Tap or scan to begin."

· Product selection: Touch a product on‑screen (or use the retained
physical keypad). The screen shows nutritional info, ingredients, and
price.

· Payment: "Tap phone / card here" (NFC), or "Scan QR to pay with
phone." The QR code leads to a mobile‑first web payment page (one‑page,
no app needed, supports Apple Pay, Google Pay, and manual card entry via
Stripe Elements). Language auto‑detection based on browser settings.

· Vend & feedback: After successful payment, the screen shows "Enjoy!"
and a quick 1‑5 star satisfaction survey. If a product fails to vend, a
"Help" button appears, and an automatic refund is triggered.

· Proximity wake: A PIR sensor detects a person approaching and wakes
the screen from low‑power idle, showing a welcoming message.

5.2 Route Driver / Restocker Interface

Drivers interact with the machine via a smartphone app (or the machine's
own screen) after authenticating with an NFC badge or PIN.

· Restock mode: The machine electronically unlocks (via MDB command).
The screen displays a planogram---which coils are empty, which products
are low, and recommended product placement based on sales data.

· Waste management (cold food): For refrigerated machines, the system
tracks expiration dates (entered during restocking or scanned via
barcode) and flags items approaching expiry, suggesting markdowns.

· Cash collection: If the cash acceptor is telemetry‑capable, the system
reports the cash box level and prompts the driver to collect, logging
the amount.

· Efficiency: Real‑time inventory (when weight sensors are installed)
eliminates manual counts and optimises restocking routes---drivers only
visit machines that actually need service.

5.3 Owner / Operator Interface

A Progressive Web App (PWA) accessible from any device (desktop, tablet,
phone). No app store install required.

· Dashboard: Revenue trends, per machine, per product. Inventory levels.
Machine health status (compressor, vibration, temperature). Advertising
impressions and revenue.

· Alerts: Push/SMS for machine offline, stockout on high‑margin items,
compressor failure (temperature spike), tamper events (door opened
outside restock hours), and abnormal refund rates.

· Pricing & promotions: Remotely adjust prices, set time‑of‑day
multipliers (e.g., evening premium), create limited‑time discounts, and
push updates to any machine instantly.

· Data & analytics: AI‑powered recommendations for optimal product mix,
machine placement, and pricing strategies. Full transaction ledger
exportable to CSV for accounting.

\-\--

6\. Payment Architecture & Fee Comparison

6.1 Transaction Flow

1\. Customer taps NFC card/phone or scans QR code → request sent to
cloud.

2\. Cloud verifies payment via Stripe (or Square, SumUp).

3\. Cloud sends an approval token to the ESP32.

4\. ESP32 commands the MDB bus (or pulses relay for legacy machines) to
vend the product.

5\. Transaction logged; customer receives confirmation.

6.2 Fee Structure -- Why IVOS Beats Traditional Vending Payment Systems

Payment Method Typical Fees Notes

IVOS -- QR/Apple Pay via Stripe 2.9% + \$0.30 Standard e‑commerce rate;
can be reduced to 2.7% + \$0.05 for high‑volume accounts

IVOS -- NFC stored‑value card 2.9% + \$0.30 at top‑up only Pre‑loaded
cards; a \$20 load incurs one fee, then unlimited fee‑free vends

Traditional per‑machine card reader (Cantaloupe, Nayax, PayRange) 5‑8%
per transaction + \$7‑15/month per machine Higher per‑swipe cost,
monthly subscription fees, no batch capability

Coin/bill only 0% (but cash handling costs: theft, counting, bank fees,
jammed validators) Hidden costs estimated 10‑18% of cash revenue

Result: IVOS saves operators 2‑5% of gross revenue in transaction fees
compared to traditional cashless solutions, while also eliminating
monthly subscription fees.

6.3 Cloud Hosting

A single DigitalOcean droplet (\$6/month) or AWS Lightsail instance
(\$5/month) can handle the entire route of 10‑50 machines. For pilot
deployments, free‑tier serverless platforms (Vercel, Netlify Functions)
are sufficient.

\-\--

7\. Financial Analysis & Breakeven (10‑Machine Route)

Assumptions (conservative):

· Vends/day/machine: 20 (a medium‑volume machine; high‑traffic locations
can exceed 50).

· Average vend price: \$2.00 (mix of snacks and drinks).

· Monthly gross per machine: 20 × 30 × \$2 = \$1,200.

· 10 machines → \$12,000/month gross.

Cost comparison -- IVOS vs. typical per‑machine card reader network:

Item IVOS (10 machines) Traditional Card Reader (e.g., Cantaloupe)

Upfront hardware \$925 (one‑time) \$2,000‑\$5,000 (readers +
installation)

Monthly fees \$10 (cloud) \$70‑\$150 (monthly subscription)

Transaction fees \~2.9% + \$0.30 per vend (mostly batched) 5‑8% per vend

Net monthly revenue after fees \~\$11,600 (after fees) \~\$11,000 (after
higher fees)

Monthly advantage +\$600 ---

Breakeven: \$925 / \$600 = ≈ 1.5 months.

Even if the operator only enables cashless on 50% of sales in the first
month, the hardware pays for itself in 3 months. Additional income from
advertising (not included above) can accelerate this to under 4 weeks.

\-\--

8\. Comparative Analysis: IVOS vs. Existing Solutions

Feature Coin/Bill Only Per‑Machine Card Reader Basic QR App IVOS

Upfront cost (per machine) \$0 \$200‑\$500 \$100‑\$200 \$92

Monthly fee (per machine) \$0 \$7‑\$15 \$5‑\$10 \*\*\$0\*\* (only \$1
cloud)

Transaction fee 0% 5‑8% 3.9% + \$0.20 2.9% + \$0.30 (batched)

Real‑time inventory No Limited (DEX) No Yes (weight sensors optional)

Predictive maintenance No No No Yes (vibration, current, temp)

Dynamic pricing No No No Yes (time‑of‑day, promotions)

Advertising revenue No No No Yes (screen ad network)

Offline operation Yes Partial No Full (local queue)

Driver/restocker app No Limited No Yes (planogram, waste mgmt)

Owner analytics None Basic Basic AI‑driven insights

\-\--

9\. Deployment Phases

Phase 1: Cashless Only (1 hour per machine)

1\. Assemble ESP32 + MDB adapter + display + NFC reader on a bench;
flash firmware.

2\. Install the assembly inside the machine; connect to MDB port and
power.

3\. Configure Stripe account and product catalogue in the cloud
dashboard.

4\. Test QR code → payment → vend flow. Verify cash fallback still
works.

5\. Repeat for all machines on the route.

Phase 2: Sensors & Telemetry (Week 2‑3)

1\. Attach vibration sensor, current clamp, door switch, and PIR.

2\. Enable sensor streaming to cloud; set basic alert thresholds.

3\. Train route drivers on the mobile app for restocking.

Phase 3: Advertising & Dynamic Pricing (Month 2+)

1\. Enable the screen's ad carousel. Sign up for a digital signage
network or sell local ads directly.

2\. Activate dynamic pricing rules (e.g., discount during slow hours,
premium during peak).

3\. Begin per‑coil weight sensor pilot on 1‑2 machines to evaluate
inventory accuracy gains.

\-\--

10\. Secondary Capabilities (No Additional Hardware)

The sensor and connectivity suite in IVOS automatically creates free
secondary features, identical in principle to those of the ILOS
laundromat system:

\# Capability Enabling Component

1 Footfall analytics (conversion rate) PIR sensor + transaction data

2 Tamper detection / break‑in alerts Door switch + vibration +
microphone

3 Cold‑chain compliance documentation Temperature log

4 Energy cost per vend Current clamp data × electricity rate

5 Product popularity ranking Weight sensors + sales data

6 Cash box fullness prediction Cash acceptor telemetry (if available)

7 Proximity marketing (BLE beacons) ESP32 Bluetooth

8 Glass‑break detection Microphone

9 Auto screen brightness / night mode Ambient light sensor

10 Free customer Wi‑Fi (optional) ESP32 Wi‑Fi

11 Anonymous cross‑operator benchmarking Cloud data aggregation

12 Warranty claim support Full sensor logs

\-\--

11\. Risks and Mitigations

Risk Mitigation

Customer reluctance to use QR/NFC Retain all original payment methods;
offer "tap‑and‑go" NFC cards as a bridge.

Internet outage ESP32 caches transactions locally; syncs when back
online. Cash still works.

Vandalism of screen Polycarbonate shield; vandal‑resistant help button.

MDB compatibility issues Adapter tested against major manufacturers;
optocoupler/relay fallback for non‑MDB machines.

Payment processor changes Multi‑processor support (Stripe, Square) built
in.

\-\--

12\. Appendix: Conceptual Expansion -- The Local Access Card (LAC)

The same NFC card issued at a vending machine (or laundromat, or coffee
shop) can be accepted across an entire network of local businesses,
using an identical \$30 ESP32‑PN532 terminal. This transforms a
single‑purpose payment token into a community currency and identity
card, unlocking:

· Cross‑business loyalty and promotions.

· Micro‑lending and pay‑advance for regular users.

· Disaster‑resilient offline payment.

· Digital identity for the unbanked.

· Intergenerational support (family loading cards remotely).

A separate white paper, "The Local Access Card: From Single‑Machine
Payment to Community Infrastructure," details the full expansion
architecture, non‑zero‑sum economics, and psychological drivers of this
network effect. IVOS is the launch point for that larger ecosystem.

\-\--

13\. References & Sourcing Guide

· ESP32‑S3: Available on Amazon, Mouser, AliExpress. Look for "ESP32‑S3
DevKitC‑1" or "ESP32‑S3 N16R8."

· 5″ TFT LCD: Search "5 inch TFT 800×480 capacitive touch" on
AliExpress; many sellers bundle with SPI driver.

· MDB adapter: NAYAX provides a commercial MDB‑USB bridge. For DIY: the
MDB protocol spec (v4.3) is public; level‑shifting circuits can be built
with a MAX3485 or similar RS‑485 transceiver.

· PN532 NFC module: Widely available on Amazon, Adafruit ("Adafruit
PN532 NFC/RFID Controller Shield" or bare module).

· Sensors: SW‑420 vibration, SCT‑013‑000 current clamp, DS18B20
temperature, MC‑38 door switch, AM312 PIR -- all commodity parts.

· Stripe integration: Use Stripe's API or the Stripe Terminal SDK for
in‑person payments. For QR, Stripe Payment Links can be a quick MVP.

· Cloud hosting: DigitalOcean, AWS Lightsail, or free‑tier
Vercel/Netlify for serverless functions.

\-\--

End of White Paper.
