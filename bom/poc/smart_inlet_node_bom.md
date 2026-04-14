# IX-Bayanihan Smart Inlet Node Proof-of-Concept BOM

## Purpose

This document defines the **proof-of-concept bill of materials** for the **IX-Bayanihan Smart Inlet Node**.

This BOM is for a **field-capable proof of concept**, not a decorative prototype.

The build is intended to help detect and report flood-relevant local drainage conditions such as:

- rising water near a curb inlet or drain
- persistent ponding near an intake
- probable blockage or poor drainage performance
- local node health degradation
- need for inspection, clearing, or maintenance

This BOM is designed to be practical, reproducible, and understandable.

---

## Scope Boundary

This BOM is for a **single Smart Inlet Node**.

It is designed for:

- curb inlets
- roadside drains
- small sumps
- alley drainage points
- low roadside collection areas
- underpass approach drains

It is **not** designed for:

- major pump stations
- large civil drainage structures
- life-safety-certified warning systems
- direct mains-voltage switching
- submerged long-duration deployment without additional engineering hardening

---

## Deployment Tier

This BOM is aimed at the space between:

- **Tier 1 bench validation**
- **Tier 2 field pilot**
- with optional upgrades toward **Tier 3 hardened community node**

The default posture is:

> **Build one serious field pilot node that can be tested outdoors, serviced, logged, and improved honestly.**

---

## Smart Inlet Node Functional Summary

The proof-of-concept Smart Inlet Node should support these minimum functions:

- water-level detection
- threshold state handling
- local visible status
- local event logging
- basic telemetry
- power-state awareness
- degraded-mode handling
- maintenance-needed flagging

---

## Node Architecture Summary

The Smart Inlet Node is built from eight subsystem groups:

1. Controller and storage
2. Water and health sensing
3. Local status output
4. Communications
5. Power subsystem
6. Enclosure and protection
7. Mounting hardware
8. Wiring, connectors, and service hardware

This BOM follows that structure.

---

## BOM Use Notes

This document uses the following criticality classes:

- **Class A — Mission Critical**
- **Class B — Strongly Important**
- **Class C — Helpful but Optional**

This document also uses the following cost posture language:

- **Low-cost**
- **Moderate-cost**
- **Hardened**

No universal price claims are made here because availability and cost vary by country, distributor, taxes, shipping, and local supply conditions.

---

# BOM Table

| Item | Subsystem | Part Description | Function | Qty | Preferred Specification | Acceptable Alternatives | Criticality | Tier Fit | Notes |
|---|---|---|---|---:|---|---|---|---|---|
| 1 | Controller | ESP32 dev board with USB programming | Main control, logging, state logic, telemetry | 1 | ESP32-WROOM or equivalent with stable 3.3V logic support | Industrial ESP32 carrier, STM32 board, RP2040 board if firmware is adapted | A | Tier 1–2 | Good starting point for low-power node development |
| 2 | Storage | microSD card module | Local event logging | 1 | SPI microSD breakout with stable logic-level support | Onboard flash logging if sufficient and documented | A | Tier 1–2 | Local logs must survive communications loss |
| 3 | Storage Media | microSD card | Log storage | 1 | Industrial or high-endurance microSD, 8 GB or higher | Smaller card if write endurance is acceptable | B | Tier 1–3 | Prefer durable card over large-capacity consumer card |
| 4 | Timekeeping | RTC module | Stable timestamping during power changes | 1 | DS3231-class RTC | Network time sync with fallback if console architecture supports it | B | Tier 1–2 | Strongly recommended for clean event reconstruction |
| 5 | Primary Water Sensor | Waterproof ultrasonic or compact radar level sensor | Detect water rise near inlet | 1 | Outdoor-capable, splash-tolerant, short-range level sensing | Pressure transducer in stilling tube, non-contact level sensor | A | Tier 1–2 | Non-contact is preferred for dirty inlet environments |
| 6 | Secondary Threshold Sensor | Float switch or simple wet threshold sensor | Secondary confirmation or fail-safe threshold detection | 1 | Sealed float switch or rugged water-presence switch | Conductive threshold probe only for controlled tests | B | Tier 1–2 | Adds confidence when primary sensor is uncertain |
| 7 | Health Sensor | Temperature/humidity sensor inside enclosure | Detect enclosure stress and moisture risk | 1 | Digital temp/RH sensor suitable for electronics enclosure monitoring | Simpler humidity alarm device | B | Tier 1–3 | Helps distinguish sensor fault from enclosure failure |
| 8 | Power Monitor | Voltage divider or power monitor module | Battery and supply-state awareness | 1 | Stable ADC-friendly battery sensing path | Dedicated I2C power monitor | A | Tier 1–3 | Required for low-power and degraded-mode behavior |
| 9 | Local Indicator | High-brightness LED indicator set | Local state visibility | 1 set | At least 2–3 visible status LEDs or a multicolor LED | Small sealed status beacon | A | Tier 1–3 | Node should remain interpretable without dashboard |
| 10 | Local Audio Alert | Piezo buzzer | Optional local audible alert | 1 | Low-power piezo buzzer | Omit if deployment context does not support sound | C | Tier 1–2 | Do not default to noise-heavy behavior in community settings |
| 11 | Communications | LoRa module or LoRa-capable ESP32 variant | Low-bandwidth field telemetry | 1 | 915 MHz hardware for U.S. testing or region-appropriate legal band | LoRaWAN variant, Wi-Fi for bench, LTE for special pilots | B | Tier 2–3 | Start simple and legal for target deployment region |
| 12 | Antenna | Compatible antenna for selected radio | Improve field communications | 1 | Tuned antenna matched to radio module and local band | Enclosure-safe stub antenna | B | Tier 2–3 | Poor antenna choice can ruin an otherwise good node |
| 13 | Battery | LiFePO4 battery pack | Safe field-capable energy storage | 1 | 6.4V or 12.8V LiFePO4 pack sized to node power budget | 18650 pack with proper BMS for controlled pilots only | A | Tier 2–3 | LiFePO4 is preferred for safety and longevity |
| 14 | Solar Panel | Compact solar panel | Battery replenishment for pilot deployment | 1 | Outdoor panel matched to charge controller and expected load | Bench DC supply for Tier 1 only | B | Tier 2–3 | Only useful where sunlight exposure is realistic |
| 15 | Charge Controller | Solar charge controller for LiFePO4 | Manage charging safely | 1 | LiFePO4-compatible controller | Valid alternative with documented settings | A | Tier 2–3 | Do not pair random controllers with battery chemistry blindly |
| 16 | DC Regulation | Buck converter or regulated power board | Stable voltage rails for controller and peripherals | 1 | Stable low-noise DC regulation with suitable current margin | Dedicated multi-output power board | A | Tier 1–3 | Power instability destroys trust quickly |
| 17 | Protection | Inline fuse | Overcurrent protection | 1 | Replaceable inline fuse sized to expected load | Resettable fuse if properly sized | A | Tier 2–3 | Minimum electrical discipline |
| 18 | Protection | TVS diode or surge suppression | Protect low-voltage electronics from transient spikes | 1 | Appropriate low-voltage transient suppression for supply path | Equivalent surge protection network | B | Tier 2–3 | Strongly recommended for outdoor wiring |
| 19 | Protection | Reverse-polarity protection path | Prevent damage from wiring mistakes | 1 | Diode or MOSFET-based reverse-polarity protection | Integrated protected power board | A | Tier 1–3 | Field mistakes happen |
| 20 | Enclosure | IP-rated polycarbonate or ABS enclosure | Main electronics housing | 1 | Outdoor-capable sealed enclosure with cable gland support | UV-stable junction box | A | Tier 2–3 | Must support service access without destructive opening |
| 21 | Sensor Shield | Splash guard or sensor hood | Reduce direct splash and debris impact on sensor | 1 | Corrosion-resistant simple guard | 3D-printed UV-stable part, bent sheet bracket | B | Tier 2–3 | Sensor survival matters more than looks |
| 22 | Cable Entry | Cable glands | Protect wiring ingress points | 2–6 | IP-rated cable glands matched to cable diameter | Equivalent sealed strain-relief fittings | A | Tier 2–3 | Do not leave ad hoc cable holes |
| 23 | Connectors | Screw terminal blocks or sealed connectors | Serviceable wiring and sensor replacement | As needed | Locking or screw-secured low-voltage connectors | JST-style connectors for enclosed indoor testing only | B | Tier 1–3 | Prefer serviceable field wiring over fragile jumper logic |
| 24 | Wiring | Outdoor-rated stranded hook-up wire | Internal and external low-voltage wiring | As needed | Color-coded stranded wire, suitable gauge for current path | Equivalent field-appropriate wire | A | Tier 1–3 | Label conductors clearly |
| 25 | Mounting Plate | Internal mounting backplate | Secure electronics inside enclosure | 1 | Non-conductive plate or standoffs | Aluminum plate with proper isolation | B | Tier 1–3 | Avoid loose electronics inside enclosure |
| 26 | Fasteners | Stainless screws, nuts, washers | Assembly and serviceability | Assorted | Stainless preferred for wet environments | Coated fasteners for short-term pilots | B | Tier 2–3 | Corrosion matters fast outdoors |
| 27 | External Mount | Pole, wall, curb, or bracket mount hardware | Install node near monitored site | 1 set | Stainless clamps, masonry anchors, or bracket hardware matched to site | Temporary pilot strap system for dry-run only | A | Tier 2–3 | Mount stability is part of system reliability |
| 28 | Labeling | External ID label and internal wiring label | Service clarity and traceability | 1 set | UV-resistant printed label set | Laminated printed labels | B | Tier 1–3 | Every field node needs a clear identity |
| 29 | Maintenance Access | Service tool kit note | Supports repeated safe opening and inspection | 1 set | Screwdriver, hex key, torque note, cleaning brush, microfiber cloth | Equivalent local field kit | C | Tier 2–3 | Treated as part of deployment package, not electronics |
| 30 | Seal Materials | Gasket check, silicone-free sealing accessories where needed | Maintain enclosure integrity | As needed | Manufacturer-supplied gasket plus approved fitting seals | Equivalent service-safe sealing components | B | Tier 2–3 | Do not rely on random adhesive blobs as a design method |

---

# Subsystem Guidance

## 1. Controller and Logging Subsystem

### Required Minimum
- microcontroller
- local storage
- repeatable boot behavior
- recoverable firmware flashing path

### Recommended Configuration
For the proof-of-concept Smart Inlet Node, the cleanest starting point is:

- ESP32-class controller
- microSD local logging
- RTC for timestamping
- watchdog-enabled firmware design

### Why This Configuration
It is simple enough to build, common enough to source, and capable enough to support:
- sensor reads
- state logic
- local alerts
- logging
- radio uplink
- degraded-mode behavior

---

## 2. Water and Condition Sensing Subsystem

### Primary Sensor Preference
The default preferred path is a **non-contact water-level sensor** mounted so it observes water rise without sitting directly in the dirtiest flow path.

This is preferred because direct-contact sensors in storm drains and curb inlets often suffer from:
- sediment
- trash contact
- bio-growth
- hard-to-clean positioning

### Secondary Sensor Preference
A simple sealed float switch is strongly recommended as a secondary threshold or sanity-check channel.

This helps the node distinguish between:
- likely real water rise
- strange primary sensor behavior
- ambiguous readings near the threshold boundary

### Optional Future Additions
Not required for this proof of concept:
- differential pressure path across a screen
- camera-assisted debris observation
- rain gauge correlation
- tilt/tamper switch

Those may come later.

---

## 3. Local Alerting and Status Subsystem

The proof-of-concept node should remain understandable without a dashboard.

### Minimum Requirement
At minimum, the node should support visible local indication for:
- power alive
- normal/watch/alert state
- degraded/fault state

### Recommended Simple Mapping
A practical starter approach is:
- green = normal
- yellow = watch
- red = alert
- blue or distinct blink = degraded/fault/service

This mapping belongs in the assembly and firmware files later, but the BOM must support it.

---

## 4. Communications Subsystem

### Default Recommendation
For a proof-of-concept field pilot, prefer:
- LoRa or LoRa-capable controller for low-bandwidth field telemetry
- local log preservation when communication is unavailable

### Why
Flood nodes should not become useless just because radio conditions are poor.

The correct posture is:
> **log first, uplink when possible**

### Acceptable Simplification
For indoor testing or very early bench work, Wi-Fi is acceptable if it speeds development.

It should not be treated as the final field assumption.

---

## 5. Power Subsystem

### Default Field Power Recommendation
The preferred Tier 2 proof-of-concept power stack is:

- LiFePO4 battery
- LiFePO4-compatible charge control
- compact solar panel where sunlight exposure is realistic
- buck regulation for electronics
- fuse
- reverse-polarity protection
- voltage-state monitoring

### Why This Matters
The node must be able to:
- survive short outages
- log events during unstable weather
- enter degraded mode intelligently as battery declines

### What Not to Do
Do not build the proof-of-concept node around:
- unprotected loose lithium cells
- random USB battery banks with unknown behavior
- mains-powered unsafe outdoor adapters
- ad hoc charging arrangements
- undocumented power switching tricks

---

## 6. Enclosure and Physical Protection Subsystem

### Minimum Physical Requirements
The enclosure must support:
- weather resistance
- cable strain relief
- service opening and closing
- internal mounting stability
- external identification labeling

### Sensor Placement Priority
The sensor should be mounted so that it can:
- observe useful water change
- avoid direct constant trash strike
- remain inspectable
- be cleaned without destroying the node

### Serviceability Priority
A node that cannot be opened, checked, and re-sealed cleanly is not ready for flood-prone deployment.

---

## 7. Mounting Subsystem

### Mounting Goal
The Smart Inlet Node must be mountable near the observed inlet or drain without:
- blocking water flow
- creating a trip hazard
- becoming impossible to service
- being destroyed by the first minor impact

### Practical Mounting Options
Depending on site conditions, acceptable proof-of-concept mounting may include:
- wall bracket
- pole clamp
- curbside protected anchor
- nearby protected post
- elevated side mount with sensor facing monitored area

### What to Avoid
Do not mount the enclosure:
- where vehicles strike it easily
- inside the heaviest trash path
- where field crews cannot reach it safely
- where opening the enclosure requires stepping into unsafe water

---

# Recommended Default Build Profile

For the first serious Smart Inlet Node proof of concept, the strongest practical build profile is:

## Controller
- ESP32-class board

## Logging
- microSD + RTC

## Primary Sensor
- waterproof ultrasonic or compact non-contact level sensor

## Secondary Sensor
- sealed float switch

## Local Status
- multistate LED indicator

## Communications
- LoRa-capable module or board

## Power
- LiFePO4 battery + solar + charge controller + low-voltage protection

## Enclosure
- IP-rated weather-resistant box with cable glands

## Mounting
- corrosion-resistant bracketed external mount

This is the cleanest balance of:
- realism
- cost control
- field usefulness
- reproducibility
- believable value

---

# Critical Components Checklist

The Smart Inlet Node should not advance to field pilot without all Class A items present and verified.

## Class A — Mission Critical
- controller
- primary sensor
- local event logging
- power regulation
- battery or stable power source
- fuse or overcurrent protection
- reverse-polarity protection
- enclosure
- cable protection
- mounting system

## Class B — Strongly Important
- RTC
- secondary threshold sensor
- communications module
- antenna
- temperature/humidity sensor
- surge protection
- service labels

## Class C — Helpful but Optional
- buzzer
- optional camera
- advanced sensor shield variant
- extra local display hardware

---

# Suggested Spare Parts for Pilot Deployment

A serious pilot should not deploy only one of everything.

Recommended spares include:

- 1 spare primary sensor
- 1 spare float switch
- 1 spare controller board
- 1 spare SD card
- spare cable glands
- spare fuses
- spare fasteners
- spare connectors
- spare mounting hardware
- spare wiring leads

Field learning goes much faster when one damaged part does not kill the whole deployment.

---

# Assembly Dependencies

This BOM depends on additional files that should follow later in the repository:

- Smart Inlet Node assembly walkthrough
- Smart Inlet Node wiring guide
- Smart Inlet Node maintenance checklist
- node status schema
- event log schema
- proof-of-concept test checklist

The BOM alone is not sufficient for a serious build.

---

# Builder Notes

## For Low-Skill Early Builders
Start with:
- bench power
- no solar
- no outdoor mount
- no radio
- simple LED states
- one primary sensor
- one log path

Then move outward carefully.

## For Serious Field Pilot Builders
Use:
- real enclosure
- real mount
- local logs
- battery-backed power
- at least one redundant threshold path
- site labels
- service notes from day one

---

# Known Limitations of This BOM

This proof-of-concept BOM does not yet include:

- final part numbers by region
- final wiring harness design
- final enclosure drawings
- final mounting drawings
- final firmware mapping
- final threshold tuning
- final channel or gateway integration
- certified surge or lightning protection design
- fully hardened anti-vandal design

That is intentional.

This BOM is the first buildable step, not the end state.

---

# BOM Acceptance Criteria

This BOM should be considered usable only if the builder can answer yes to all of the following:

- Can I identify each subsystem clearly?
- Can I tell which parts are mission critical?
- Can I understand the preferred build path?
- Can I see which items are optional versus necessary?
- Can I build a real field pilot from this list with the later assembly guide?
- Can I avoid making claims this build does not support?

If the answer is yes, the BOM is doing its job.

---

# Summary

This Smart Inlet Node proof-of-concept BOM is designed to create a **credible first field node** for IX-Bayanihan.

It is meant to be:

- open
- modular
- honest
- field-aware
- serviceable
- expandable

Its role is simple but important:

> **Detect local flood-relevant drainage trouble early enough and clearly enough to improve visibility, maintenance targeting, and response decisions at real street-level trouble points.**

That is a serious and useful starting point.
