White Paper: Integrated Laundromat Operating System (ILOS)

A Low‑Cost, Retrofit Platform for Cashless Payment, Preventive
Maintenance, and Passive Revenue

Version 2.1 -- Grounded Edition

Author: Independent Concept Development

Date: June 2026

\-\--

1\. Abstract

The Integrated Laundromat Operating System (ILOS) is a modular,
ESP32‑based retrofit platform that transforms legacy coin‑operated
laundries into connected, multi‑revenue businesses. ILOS replaces
per‑machine coin drops and expensive third‑party card readers with a
unified QR‑code payment gateway, an NFC stored‑value card system, an
attendant‑facing tablet console, and a cloud backend. The same hardware
stack adds machine health sensors (vibration, current, door) and drives
high‑brightness displays, enabling predictive maintenance, dynamic
pricing, and passive advertising income. Built entirely from commodity
electronics and open‑source software, a 20‑machine installation costs
under \$1,600 in parts---less than a single month's fees of a typical
card‑reader network---and can be self‑installed in a weekend. This paper
provides a complete, grounded bill of materials with real‑world
sourcing, step‑by‑step interface instructions, human‑centred design
flows, and a rigorous financial comparison against existing solutions.
All figures are based on published rates and publicly available
component prices as of 2026.

\-\--

2\. System Overview

ILOS equips each machine with an ESP32‑S3 microcontroller (Wi‑Fi +
Bluetooth), a sunlight‑readable e‑ink display, an NFC reader, and a
small relay/opto‑isolator board to interface with the machine's coin
mechanism. A central attendant tablet runs a progressive web app for
cash/card sales, NFC card encoding, and machine monitoring. The cloud
backend (lightweight VPS or serverless functions) handles payment
processing via Stripe, stores transaction logs, and serves the owner
dashboard.

The system can be deployed incrementally:

Phase Components added Time to deploy

1 -- Cashless QR only ESP32, e‑ink, relay, attendant tablet 1 weekend

2 -- Packages & NFC NFC encoder, cards, receipt printer 1--2 weeks

3 -- Sensors & Predictive Maintenance Vibration, current, door sensors;
cloud alerts Month 2

4 -- Advertising & AI Upgrade some screens to LCD; activate ad network &
analytics Month 3+

Each phase delivers standalone value; the owner may stop at any point.

\-\--

3\. Complete Bill of Materials (20‑Machine Retrofit)

All prices are per‑unit in small‑lot quantities from common online
retailers (Amazon, AliExpress, Adafruit, Mouser). Prices may vary; bulk
and local sourcing will reduce costs further.

Component Suggested Model / Search Term Qty Unit Cost Total

Microcontroller ESP32‑S3 DevKitC‑1 (Wi‑Fi, BLE) 20 \$5.00 \$100.00

E‑ink display (2.9″) Waveshare 2.9″ e‑Paper (296×128, SPI) 20 \$15.00
\$300.00

Relay module (1‑ch 5V) SRD‑05VDC or "1 channel relay module optocoupler"
20 \$3.50 \$70.00

Optocoupler board 4N35 optocoupler module with resistor (for electronic
coin acceptors) 10 \$2.50 \$25.00

MDB adapter board NAYAX MDB‑USB or build custom (CP2102 + MDB level
shifter) 5 \$30.00 \$150.00

Vibration sensor SW‑420 vibration module (digital) 20 \$1.50 \$30.00

Current clamp SCT‑013‑000 (100A) split‑core CT 10 \$8.00 \$80.00

Temperature sensor DS18B20 waterproof probe 5 \$3.00 \$15.00

Door reed switch MC‑38 magnetic door sensor 20 \$1.00 \$20.00

Help button 16mm vandal‑resistant metal push button (momentary, IP65) 20
\$3.00 \$60.00

Power supply (5V) Hi‑Link HLK‑PM01 AC‑DC 5V 0.6A step‑down module 20
\$5.00 \$100.00

Attendant tablet Refurbished Samsung Galaxy Tab A 8.0″ (or any Android
10+) 1 \$100.00 \$100.00

NFC reader/writer ACR122U USB NFC Reader (for encoding cards) 1 \$40.00
\$40.00

NFC cards (blank) NTAG215 PVC cards (pack of 100) 200 \$0.30 \$60.00

Bluetooth receipt printer Star Micronics SM‑S220i (or compatible 58mm
thermal) 1 \$50.00 \$50.00

Stripe card reader Stripe Reader M2 (pre‑certified) 1 \$59.00 \$59.00

Wiring & connectors Assorted Dupont wires, terminals, heat‑shrink --
\$40.00 \$40.00

TOTAL \$1,299.00

Note: Many parts (ESP32s, relays, sensors, displays) can be bought in
bulk packs for 20--40% less on AliExpress; the above uses conservative
single‑unit prices. Cloud hosting is not included; see §6.3.

\-\--

4\. Machine Interface: Connecting ILOS to Every Generation of Washer &
Dryer

The most critical physical layer is the link between the ESP32 and the
machine's start mechanism. ILOS works in parallel with the original coin
acceptor, preserving cash as a fallback.

4.1 Legacy Coin‑Slide Machines

These units use a mechanical slide that trips a microswitch; each coin
drop sends a short circuit closure. ILOS connects a relay module across
the same microswitch terminals. When the cloud confirms a payment, the
ESP32 pulses the relay for 50 ms per "virtual coin" ---the machine's
accumulator tallies the pulses and enables the cycle.

Parts needed: 1 relay module per machine, wired in parallel to the
existing coin switch. No software changes to the machine.

4.2 Electronic Coin Acceptors (e.g., CoinCo, Mars)

These output a digital pulse train (often 12 V or 24 V). ILOS uses an
optocoupler board to isolate the ESP32's 3.3 V logic and replicate the
exact pulse protocol. The number of pulses per wash and the pulse width
are configurable in the ESP32 firmware.

Parts needed: 1 optocoupler module. Test the coin acceptor's output
voltage before wiring; a 4N35 with appropriate current‑limiting resistor
works for most units.

4.3 Modern MDB‑Ready Machines (Dexter, Speed Queen, Huebsch, etc.)

These communicate via the industry‑standard Multi‑Drop Bus (MDB). ILOS
uses an MDB‑to‑UART adapter (commercial boards exist from NAYAX, Crane,
or custom builds using an MDB level‑shifter circuit and a CP2102
USB‑UART bridge). The ESP32 sends MDB commands to impersonate a
"cashless device," authorising vends, reading machine status, and even
selecting cycle options on capable machines.

Parts needed: 1 MDB adapter per MDB machine. Only needed for machines
that have an MDB port (typically models from 2015 onward). Older
machines simply use the relay/optocoupler method.

4.4 Dual‑Mode & Fail‑Safe

All connections are opto‑isolated or relay‑based and wired in parallel.
If the ESP32 loses power, the coin mechanism works exactly as before. If
the cloud connection drops, the ESP32 can still vend offline using
stored tokens (see §6.2).

\-\--

5\. Human‑Machine Interface (HMI)

ILOS treats the customer, attendant, and owner as equal subsystems.
Every interface is tailored to the user's goal, technical literacy, and
physical context.

5.1 Customer Experience

At the machine:

· The e‑ink display is mounted at eye level, behind a polycarbonate
window. It cycles through three states:

· IDLE: Large QR code, machine number, current price, and a "Need help?"
icon.

· PAID: Green checkmark, "Machine X is yours -- press START within 2
minutes."

· RUNNING: Countdown timer and "Your laundry will be done at HH:MM."

· DONE: Flashing "Please remove your laundry."

· FAULT: Error description and "Attendant notified."

· A rugged help button below the screen sends a push notification to the
attendant tablet with the machine number and fault code.

Web payment page (after QR scan):

· Single‑page, no‑scroll design. Browser language auto‑detection
(English, Spanish, etc.).

· One‑tap Apple Pay / Google Pay, or manual card entry via Stripe
Elements.

· No account creation. No app install.

· After payment, the page shows a confirmation code and instructions. If
the machine doesn't start (door open, jam), the system auto‑refunds via
Stripe.

NFC card usage:

· Customers tap their pre‑loaded card directly on the machine's PN532
reader. The display confirms balance and deducts the cycle cost in real
time.

5.2 Attendant Dashboard (Tablet)

A Progressive Web App (PWA) accessible from the attendant's tablet. Main
screen:

· Machine grid: Icons colour‑coded green (available), blue (running),
yellow (cycle complete), red (fault). Tapping a machine shows payment
history, error codes, and one‑touch actions.

· Quick‑action panel: "Sell Package," "Issue NFC Card," "Process Cash
Payment," "Refund."

· Cash sale flow: Attendant selects package → taps "Cash" → optionally
encodes a new NFC card or loads value on an existing one → receipt
prints automatically.

· Help button response: When a customer presses a help button, the
tablet vibrates and highlights the machine in red, showing the fault
details and suggested resolution.

· Offline mode: Tablet stores a local queue of transactions; syncs with
cloud when connectivity returns.

5.3 Owner Dashboard (PWA)

Available on any device. After email‑based magic‑link authentication,
the owner sees:

· Revenue trends: Daily/weekly/monthly, per machine and per payment
method.

· Machine health: Vibration history, compressor current, temperature
logs for refrigerated units. Predictive alerts ("Machine 4 bearings
degrading -- schedule service in 2‑3 weeks").

· Advertising performance: Impressions, revenue, active campaigns.

· Dynamic pricing controls: Set base prices, time‑of‑day multipliers,
and promotions.

· Full transaction ledger: Searchable, exportable to CSV for accounting.

· Proactive SMS/email alerts for: revenue anomalies, machine offline,
tamper detected, refund issued, maintenance required.

\-\--

6\. Payment Architecture & Fee Comparison

6.1 How Transactions Flow

1\. Customer scans QR or taps NFC → encrypted request sent to cloud.

2\. Cloud verifies payment via Stripe (or could use Square, SumUp).

3\. Cloud instructs the ESP32 to pulse the relay/MDB command and start
the cycle.

4\. Transaction recorded in ledger; customer receives confirmation.

6.2 Fee Structure -- Why ILOS Beats Per‑Swipe Readers

Payment Method Typical Fee Notes

Stripe (online wallet / card) 2.9% + \$0.30 Industry‑standard for
web‑based payments

ILOS package batching (e.g., \$20 for 10 washes) 2.9% + \$0.30 once
Saves \~\$2.70 in fees vs. 10 individual swipes

NFC card (pre‑loaded) 2.9% + \$0.30 at top‑up One fee per load;
subsequent taps are free

Per‑machine card reader (CleanPay, SpyderWash, PayRange) 5--8% per
swipe + \$20--40/machine monthly Industry‑standard rates; no batching
possible

Coin‑only 0% (but shrinkage, counting labour, theft) Hidden costs
estimated at 8--15% of gross

Result: For a laundromat processing \$3,000/month in cycle revenue, ILOS
saves \$150--\$300/month in transaction costs alone vs. per‑machine card
readers, while adding package‑based loyalty.

6.3 Cloud Hosting Costs

A small DigitalOcean droplet (\$6/month) or AWS Lightsail instance
(\$5/month) can easily handle the traffic for a 20‑machine location. For
the first pilot, a free‑tier cloud function (Vercel, Netlify Functions,
Cloudflare Workers) may suffice. Budget \$10/month for hosting and
database.

\-\--

7\. Financial Analysis & Breakeven (20‑Machine Location)

Assumptions (conservative):

· Average cycles/day/machine: 3 (many laundromats average 2--5).

· 20 machines: 60 cycles/day.

· Average revenue/cycle: \$3.00 (blend of washers at \$2.50 and dryers
at \$1.50, plus occasional larger machines).

· Monthly gross cycle revenue: 60 × 30 × \$3 = \*\*\$5,400\*\*.

Cost comparison -- ILOS vs. leading card reader network:

Item ILOS CleanPay / similar

Upfront hardware \$1,299 (one‑time) \$6,000--\$12,000 (one‑time)

Monthly recurring fees \$10 (cloud) \$400--\$800 (20 machines × \$20‑40)

Transaction fees 2.9% + \$0.30 (mostly batched) 5--8% per swipe

Net monthly revenue after fees \$5,400 -- (\$5,400×0.029 + \~\$200 in
per‑transaction fees when batching) ≈ \*\*\$5,040\*\* \$5,400 --
(\$5,400×0.065) -- \$600 = \*\*\$4,449\*\*

ILOS advantage: \~\$591/month more net revenue.

Breakeven: \$1,299 / \$591 = ≈ 2.2 months.

Even if only half the customers adopt cashless in the first year, the
hardware pays for itself within 6 months on transaction savings alone.
Additional income from advertising and dynamic pricing (not included
above) shortens this further.

\-\--

8\. Comparative Analysis: ILOS vs. Existing Solutions

Feature Coin‑Only Per‑Machine Card Reader Basic QR App (PayRange) ILOS

Upfront cost (20 machines) \$0 \$5,000--\$10,000 \$2,000--\$4,000
\$1,300

Monthly fees \$0 \$400--\$800 \$200--\$400 \$10

Per‑transaction fee n/a 5--8% 3.9% + \$0.20 2.9% + \$0.30 (batched)

Package / loyalty support No Limited Some Full (NFC, packages, dynamic
pricing)

Machine health monitoring No No No Vibration, current, temperature

Advertising revenue No No No Yes (up to \$150/machine/mo)

Offline operation Yes Usually not Limited Full (local queue, sync later)

Owner data & analytics None Basic Basic AI‑driven insights, predictive
maintenance

Fallback to cash Yes Yes No (app‑only) Yes, parallel coin mech

ILOS is the only system that offers a complete suite of capabilities at
a fraction of the cost, without locking the owner into a proprietary
network.

\-\--

9\. Deployment Plan (Step‑by‑Step)

Phase 1 -- QR‑Only Cashless (Weekend 1)

1\. Assemble ESP32 + e‑ink + relay modules on a bench; test with a 5V
supply and a simulated coin switch.

2\. Create Stripe account, set up a simple product page (use a static
site generator or Stripe Payment Links as MVP).

3\. Install one unit on a test washer; wire relay parallel to coin
switch.

4\. Generate QR code and attach to machine. Test full payment → vend
flow.

5\. Once verified, replicate on all machines (approx. 30 minutes each).

6\. Attendant tablet: open PWA from browser; no additional setup needed.

Phase 2 -- Packages & NFC (Week 2‑3)

1\. Add PN532 NFC reader to machines (SPI connection to ESP32).

2\. Connect NFC encoder (ACR122U) to attendant tablet via USB‑OTG.

3\. Issue blank NFC cards to regular customers; demonstrate
load‑and‑tap.

4\. Update web payment page to offer packages.

Phase 3 -- Sensors & Predictive Maintenance (Month 2)

1\. Attach vibration sensors to washer cabinets, current clamps on main
power feeds.

2\. Configure ESPHome or custom firmware to stream sensor data.

3\. Set up basic thresholds for alerts (e.g., vibration \> X for \> 5
cycles).

4\. Owner dashboard shows historical trends.

Phase 4 -- Advertising & AI (Month 3+)

1\. Swap e‑ink for 5″ TFT LCDs on high‑traffic machines (use the same
ESP32, just change display).

2\. Sign up for a digital signage network (e.g., ScreenCloud, OptiSigns)
to manage ads.

3\. Enable dynamic pricing module: set off‑peak discounts.

4\. Activate AI anomaly detection (lightweight ML on cloud or edge).

\-\--

10\. Secondary Capabilities (No Extra Hardware)

Every component of ILOS was chosen to serve multiple purposes. The
following "bleed‑off" capabilities emerge at zero additional cost:

\# Capability Enabling Component

1 Theft detection (unpaid machine use) Vibration sensor + no matching
payment record

2 Utility cost per wash (profit analytics) Current clamp data ×
electricity rate

3 Customer satisfaction mapping Help button press frequency per machine

4 Conversion funnel (footfall → paying user) QR scan count vs. completed
payments

5 Automatic loyalty rewards NFC card usage history triggers "next one
free"

6 Attendant performance metrics Tablet log: refund rate, response time

7 Off‑grid capability (solar/battery) E‑ink's ultra‑low power draw

8 Automated tax preparation Single‑click CSV export of all transactions

9 Emergency public alerts Screens can be remotely overridden for
Amber/Silver alerts

10 Warranty claim documentation Full sensor logs prove proper
maintenance

11 Multi‑location anonymous benchmarking Aggregated cloud data (opt‑in)

12 Proximity marketing ESP32 BLE beacon sends offers to nearby phones

\-\--

11\. Risks and Mitigations

Risk Mitigation

Customer resistance to QR/NFC Retain coin mech; offer NFC cards as
"digital coins"; attendant accepts cash/card at terminal.

Internet outage ESP32 queues transactions offline; syncs when back
online. E‑ink retains last QR. Attendant tablet works locally.

Hardware failure (ESP32, display) Modular design; swap‑out takes \<5
minutes. Spare units cost \<\$20 total. Coin fallback ensures no
downtime.

Vandalism Screens behind polycarbonate; help buttons are
vandal‑resistant (IP65).

Stripe policy changes Multi‑processor support built in (Square, SumUp)
for easy migration.

Legacy machine incompatibility Relay/optocoupler method works on any
coin‑operated machine; MDB adapter covers modern ones.

\-\--

12\. Appendix: The Local Access Card (Multi‑Business Expansion)

The same NFC card issued at the laundromat can be accepted at other
local businesses---coffee shops, vending machines, pharmacies---using
the identical ESP32+PN532 terminal. This creates a Local Access Card
(LAC) network. See the companion white paper "The Local Access Card: How
a Single NFC Card Becomes a Community Payment & Identity Network" for
full details. In brief:

· Businesses join the network with a \$30 terminal.

· Cardholders experience frictionless, single‑tap payment across the
neighbourhood.

· The platform earns a tiny per‑transaction fee (1% vs. 3% credit card),
saving businesses money.

· Secondary benefits: microlending, disaster currency, digital identity
for the unbanked, and intergenerational support.

· Non‑zero‑sum: every participant (consumer, merchant, platform) gains.

\-\--

13\. References & Sourcing Guide

· ESP32‑S3 boards: search "ESP32‑S3 DevKitC" on Amazon, Mouser, or
AliExpress. Bulk packs of 10 often under \$4/unit.

· E‑ink displays: Waveshare 2.9″ e‑Paper (SPI) -- available on Amazon,
Waveshare.com, and AliExpress.

· Relay modules: "1 channel 5V relay module optocoupler" -- widely
available; look for SRD‑05VDC relays.

· Optocoupler modules: 4N35 modules pre‑soldered with resistor; search
"4N35 optocoupler module".

· MDB adapter: NAYAX offers a commercial MDB‑USB bridge. For DIY: MDB
level‑shifter schematics are published in the MDB protocol specification
(MDB/ICP v4.3).

· Sensors: SW‑420 vibration module, SCT‑013‑000 current clamp, DS18B20
temperature sensor, MC‑38 door reed switch -- all found on AliExpress,
Amazon, Adafruit.

· NFC: ACR122U reader/writer for encoding; PN532 NFC/RFID module for
machines (SPI interface). Both on Amazon, Adafruit.

· NFC cards: NTAG215 PVC cards in bulk (e.g., 100‑pack on Amazon for
\~\$30).

· Thermal printer: Star Micronics SM‑S220i or any ESC/POS compatible
58mm Bluetooth printer.

· Stripe Reader M2: available directly from Stripe or Amazon.

· Cloud: DigitalOcean (\$6/month droplet) or AWS Lightsail (\$5/month).
For serverless, Vercel/Netlify Functions free tier is sufficient for
pilot.

\-\--
