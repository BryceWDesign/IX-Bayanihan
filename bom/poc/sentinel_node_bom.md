# IX-Bayanihan Channel / Outfall Sentinel Node Proof-of-Concept BOM

## Purpose

This document defines the **proof-of-concept bill of materials** for the **IX-Bayanihan Channel / Outfall Sentinel Node**.

This BOM is for a **field-capable exposed-environment monitoring node** intended to provide broader drainage context beyond a single street drain or curb inlet.

The Sentinel Node is designed to help observe and report flood-relevant corridor conditions such as:

- rising water in channels, esteros, culverts, or outfalls
- downstream submergence or poor discharge conditions
- likely backflow pressure on local drainage
- prolonged elevated water conditions
- exposed node health degradation
- need for inspection, clearing, escalation, or protective action

This BOM is designed to be practical, reproducible, and believable.

---

## Scope Boundary

This BOM is for a **single Channel / Outfall Sentinel Node**.

It is designed for deployment near:

- esteros
- drainage channels
- canal edges
- culvert mouths
- river-adjacent outfalls
- low-elevation discharge points
- tide-influenced interfaces
- backflow-prone drainage exits
- pump approach water corridors

It is **not** designed for:

- major civil floodgate actuation
- direct control of municipal pump motors
- fully submerged long-duration underwater deployment
- wave-impact marine structures without added engineering
- certified legal flood-warning infrastructure
- autonomous command over public flood-control assets

---

## Deployment Tier

This BOM is primarily aimed at:

- **Tier 2 field pilot**
- with a clear path toward **Tier 3 hardened community node**

The design posture is:

> **Build one serious exposed-environment pilot node that can survive harsh outdoor placement, preserve useful logs, and help explain why neighborhood drainage is succeeding or failing.**

---

## Sentinel Node Functional Summary

The proof-of-concept Sentinel Node should support these minimum functions:

- exposed-location water-level sensing
- time-based trend interpretation
- threshold state handling
- local visible status
- local event logging
- communications heartbeat
- power-state awareness
- degraded-mode handling
- optional backflow-context flagging
- maintenance-needed flagging

---

## Node Architecture Summary

The Channel / Outfall Sentinel Node is built from eight subsystem groups:

1. Controller and storage
2. Water, enclosure, and health sensing
3. Local status output
4. Communications and optional image support
5. Power subsystem
6. Enclosure and environmental protection
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

- **Moderate-cost**
- **Hardened**
- **District-reference**

No universal price claims are made here because cost varies by country, source, import route, shipping, taxes, and local availability.

---

# BOM Table

| Item | Subsystem | Part Description | Function | Qty | Preferred Specification | Acceptable Alternatives | Criticality | Tier Fit | Notes |
|---|---|---|---|---:|---|---|---|---|---|
| 1 | Controller | ESP32 industrial-capable dev board or equivalent | Main control, logging, state logic, telemetry | 1 | ESP32-WROOM or equivalent with stable 3.3V logic, watchdog support, and sufficient GPIO | STM32 board, RP2040 board, industrial carrier board if firmware is adapted | A | Tier 2–3 | Must support exposed-environment node logic and logging |
| 2 | Storage | microSD card module | Local event logging | 1 | Stable SPI microSD breakout with proper logic handling | Large onboard flash if endurance and retrieval are documented | A | Tier 2–3 | Sentinel node must preserve evidence during communications loss |
| 3 | Storage Media | microSD card | Local event storage | 1 | Industrial or high-endurance microSD, 8 GB or higher | Smaller capacity card if endurance is strong | B | Tier 2–3 | Prefer write endurance over consumer capacity claims |
| 4 | Timekeeping | RTC module | Stable timekeeping during unstable power | 1 | DS3231-class RTC | Network time sync with disciplined fallback where architecture supports it | B | Tier 2–3 | Strongly recommended for exposed nodes with intermittent uplink |
| 5 | Primary Water Sensor | Outdoor-capable non-contact level sensor | Measure changing water level in channel/outfall environment | 1 | Compact radar or ultrasonic sensor rated for splash-heavy outdoor use | Pressure transducer in protected stilling tube, other non-contact level sensor | A | Tier 2–3 | Non-contact is preferred for dirty, debris-prone corridors |
| 6 | Sensor Shield | Sensor rain/splash hood | Reduce direct splash, sun glare, and debris strike | 1 | Corrosion-resistant hood or bracketed shield | UV-stable printed shield, bent sheet shield | B | Tier 2–3 | Strongly recommended for exposed placements |
| 7 | Secondary Threshold Sensor | Float switch or secondary threshold sensor | Provide confirmation channel or safety threshold | 1 | Sealed float switch or rugged threshold sensor | Secondary pressure trigger in protected chamber | B | Tier 2–3 | Useful when primary sensor becomes ambiguous |
| 8 | Enclosure Health Sensor | Temperature/humidity sensor inside enclosure | Detect moisture ingress or heat stress | 1 | Digital temp/RH sensor suitable for enclosure monitoring | Simpler humidity alarm or dew indicator | B | Tier 2–3 | Very useful for distinguishing environment from electronics failure |
| 9 | Power Monitor | Voltage divider or power monitor module | Battery and supply-state awareness | 1 | Stable ADC-ready sensing path or dedicated power monitor | Equivalent monitored power board | A | Tier 2–3 | Required for degraded-mode power logic |
| 10 | Local Indicator | High-brightness sealed LED or beacon | Local visible state | 1 set | Sunlight-readable status LEDs or compact beacon | Smaller LED indicators for sheltered pilot only | A | Tier 2–3 | Sentinel nodes should remain interpretable on site |
| 11 | Local Audio Alert | Piezo or weather-tolerant buzzer | Optional audible service or alert output | 1 | Low-power buzzer in protected mounting | Omit if noise is inappropriate or power budget is tight | C | Tier 2 | Use cautiously in community or wildlife-sensitive settings |
| 12 | Communications | LoRa module or LoRa-capable board | Low-bandwidth field telemetry | 1 | Long-range low-power radio matched to legal local band | LoRaWAN variant, LTE modem for harder pilots, Wi-Fi only for controlled local testing | B | Tier 2–3 | Low-bandwidth long-range communications fit this node well |
| 13 | Antenna | External or enclosure-compatible antenna | Improve range and reliability | 1 | Tuned antenna matched to radio and local band | Protected stub antenna, higher-gain external antenna where lawful | B | Tier 2–3 | Antenna placement matters heavily at channel edges |
| 14 | Optional Camera | Low-resolution camera module in protected viewport | Visual debris or condition reference | 1 | Small camera with controlled snapshot support | Omit entirely for simpler builds | C | Tier 2–3 | Useful but optional; keep privacy and maintenance in mind |
| 15 | Camera Viewport | Transparent sealed window | Protect optional camera opening | 1 | UV-stable clear window or lens cover | Omit if no camera is used | C | Tier 2–3 | Must not compromise enclosure sealing |
| 16 | Battery | LiFePO4 battery pack | Safe field-capable energy storage | 1 | 6.4V or 12.8V LiFePO4 sized to telemetry and sensing load | Other chemistry only if protected and clearly documented | A | Tier 2–3 | Prefer safe chemistry and clear service behavior |
| 17 | Solar Panel | Outdoor solar panel | Replenish battery during pilot or community deployment | 1 | Outdoor-rated panel sized to duty cycle and seasonal conditions | Bench DC source for non-field testing | B | Tier 2–3 | Only useful if site exposure supports it |
| 18 | Charge Controller | LiFePO4-compatible solar charge controller | Safe battery charging | 1 | LiFePO4-supporting controller matched to panel and battery | Equivalent controller with verified settings | A | Tier 2–3 | Do not improvise chemistry compatibility |
| 19 | DC Regulation | Buck converter or regulated power board | Stable low-voltage rails | 1 | Low-noise regulator with current margin and thermal stability | Multi-output regulated board | A | Tier 2–3 | Stable power is essential to trustworthy logs |
| 20 | Protection | Inline fuse | Overcurrent protection | 1 | Replaceable inline fuse sized to system load | Resettable fuse if properly specified | A | Tier 2–3 | Minimum outdoor electrical discipline |
| 21 | Protection | TVS diode or surge suppression | Reduce damage from transient spikes | 1 | Appropriate low-voltage suppression on supply path | Equivalent surge network | B | Tier 2–3 | Strongly recommended for outdoor cable runs |
| 22 | Protection | Reverse-polarity protection path | Prevent wiring damage | 1 | Diode or MOSFET-based reverse-polarity design | Protected power board | A | Tier 2–3 | Field wiring mistakes must not destroy the node |
| 23 | Enclosure | IP-rated UV-stable enclosure | Main electronics housing | 1 | Outdoor-capable polycarbonate or UV-stable ABS enclosure with room for service access | Equivalent junction box with verified seal quality | A | Tier 2–3 | Must support exposed deployment and repeat opening |
| 24 | Cable Entry | Cable glands | Protect cable ingress points | 2–8 | IP-rated glands matched to cable size | Equivalent sealed strain-relief fittings | A | Tier 2–3 | No improvised cable holes |
| 25 | Connectors | Sealed serviceable low-voltage connectors | Sensor and power serviceability | As needed | Locking, moisture-resistant connectors | Screw terminals inside enclosure for sheltered segments only | B | Tier 2–3 | Prefer field replacement without rewiring everything |
| 26 | Wiring | Outdoor-rated stranded wire | Power and signal routing | As needed | UV- and moisture-tolerant stranded wire in appropriate gauge | Equivalent field wiring | A | Tier 2–3 | Route and label all conductors clearly |
| 27 | Mounting Bracket | External mount bracket | Secure enclosure to wall, rail, or post | 1 set | Stainless or coated bracket system matched to site | Heavy-duty noncorroding strap and backplate arrangement | A | Tier 2–3 | Mount stability is part of the measurement quality |
| 28 | Sensor Mount | Sensor standoff or aiming bracket | Position primary sensor correctly | 1 | Adjustable corrosion-resistant bracket | Fixed bracket if site geometry is known | A | Tier 2–3 | Sensor aim and distance matter a great deal |
| 29 | Fasteners | Stainless screws, nuts, washers | Assembly and outdoor durability | Assorted | Stainless preferred | Coated fasteners for short pilot only | B | Tier 2–3 | Corrosion becomes a real issue fast |
| 30 | Labeling | External ID label and internal wiring label | Traceability and service clarity | 1 set | UV-resistant printed label set | Laminated printed labels | B | Tier 2–3 | Every exposed node needs clear service identity |
| 31 | Mounting Isolation | Rubber or vibration-isolating washers/pads | Reduce vibration transmission and loosening | As needed | Weather-tolerant isolating pads | Omit only where mount is already rigid and sheltered | C | Tier 2–3 | Helpful near bridges, roads, or vibrating infrastructure |
| 32 | Bird / Debris Guard | Small top cover or guard | Reduce fouling and accidental impact | 1 | Corrosion-resistant simple guard | Printed UV-stable part or bent shield | C | Tier 2–3 | Helpful in dirty exposed corridors |
| 33 | Seal Materials | Gasket check and approved sealing accessories | Maintain enclosure integrity | As needed | Manufacturer gasket and approved fitting seals | Equivalent service-safe seal parts | B | Tier 2–3 | Do not treat random sealant blobs as engineering |
| 34 | Service Tools Note | Basic field service kit | Supports safe access and cleaning | 1 set | Screwdrivers, hex keys, inspection cloth, small brush, contact-safe cleaner | Equivalent local kit | C | Tier 2–3 | Belongs with deployment package even if not mounted in node |
| 35 | Optional External Level Reference | Marked fixed measuring strip or reference marker | Manual cross-check during pilot testing | 1 | Corrosion-resistant visible level marker | Painted site marker where lawful and durable | C | Tier 2 | Useful for validating sensor readings during early pilots |

---

# Subsystem Guidance

## 1. Controller and Logging Subsystem

### Required Minimum
- microcontroller
- local storage
- recoverable boot behavior
- stable fault-state persistence
- practical field reflash pathway

### Recommended Configuration
For the proof-of-concept Sentinel Node, the cleanest starting point is:

- ESP32-class controller
- microSD local logging
- RTC for timestamping
- watchdog-enabled firmware design
- strong startup self-check behavior

### Why This Configuration
The Sentinel Node lives in a harsher environment than the street node and is more likely to experience:
- intermittent radio
- splash and humidity stress
- solar variability
- unstable field service intervals

It therefore needs trustworthy local evidence even when the rest of the stack is partially blind.

---

## 2. Water and Condition Sensing Subsystem

### Primary Sensor Preference
The default preferred path is a **non-contact outdoor-capable level sensor** aimed at a known water surface region.

This is preferred because direct-contact sensing at outfalls, channels, or esteros can be degraded by:
- floating debris
- sediment
- biofouling
- turbulent surface junk
- difficult retrieval

### Secondary Sensor Preference
A secondary threshold sensor is strongly recommended for:
- sanity checking
- confirming high-water conditions
- distinguishing bizarre primary sensor behavior from plausible water rise

### Optional Camera Use
A camera is optional and should never be treated as the primary detection path.
If included, it should support:
- low-rate snapshots
- sealed viewing
- maintainable cleaning access

It should not create privacy, complexity, or power burdens that outweigh its value.

---

## 3. Local Alerting and Status Subsystem

The Sentinel Node must remain interpretable on site.

### Minimum Requirement
At minimum, it should visibly indicate:
- node alive
- normal/watch/alert state
- degraded/fault or service state

### Recommended Simple Mapping
A practical starting approach is:
- green = normal
- yellow = watch
- red = alert
- blue or distinct blink = degraded/fault/service

The exact mapping can be finalized later in firmware and assembly files, but this BOM must support visible status from the start.

---

## 4. Communications Subsystem

### Default Recommendation
For proof-of-concept field deployment, prefer:
- LoRa or equivalent long-range low-power radio
- local logs preserved regardless of uplink success
- simple heartbeat messaging instead of chatty traffic

### Why
Sentinel nodes are often placed where:
- radio paths are imperfect
- cellular may be inconsistent
- service visits are less frequent
- exposed placements make reliability more important than bandwidth

The correct posture is:
> **preserve evidence locally, transmit what matters, do not depend on constant connectivity**

### Acceptable Simplification
For early bench and dry-run work:
- Wi-Fi is acceptable
- direct laptop serial logging is acceptable
- short-range local radio is acceptable

Those should not be mistaken for a final exposed-node assumption.

---

## 5. Power Subsystem

### Default Field Power Recommendation
The preferred Tier 2 proof-of-concept power stack is:

- LiFePO4 battery
- LiFePO4-compatible charge control
- solar panel if site exposure is adequate
- stable DC regulation
- fuse
- reverse-polarity protection
- transient suppression
- battery-state monitoring

### Why This Matters
The Sentinel Node may be the only source telling you that:
- the channel is already high
- the outfall is partly submerged
- downstream conditions are worsening
- local street flooding is not just a blocked inlet problem

It must therefore remain alive through degraded conditions.

### What Not to Do
Do not build this node around:
- consumer USB power banks with undocumented sleep behavior
- loose lithium cells without proper protection
- improvised outdoor mains power
- undocumented charge boards
- mystery solar controller settings

---

## 6. Enclosure and Physical Protection Subsystem

### Minimum Physical Requirements
The enclosure must support:
- outdoor weather resistance
- cable strain relief
- repeated service access
- internal mounting stability
- external identification labeling
- protected sensor routing
- splash-aware placement

### Sensor Placement Priority
The primary sensor should be placed so that it can:
- observe a known water-surface region
- avoid constant direct impact from heavy trash
- remain inspectable
- be re-aimed or cleaned without rebuilding the node

### Serviceability Priority
A node that cannot be safely opened, inspected, resealed, and returned to service is not serious enough for exposed deployment.

---

## 7. Mounting Subsystem

### Mounting Goal
The Sentinel Node must be mounted so that it:
- stays stable
- maintains sensor alignment
- avoids obvious impact zones
- remains reachable for service
- does not obstruct flow
- does not invite needless tampering

### Practical Mounting Options
Depending on site conditions, acceptable proof-of-concept mounting may include:
- wall bracket on protected channel edge
- rail or fence mount
- post mount
- bridge-side protected bracket
- elevated outfall-side mount
- culvert-adjacent protected side mount

### What to Avoid
Do not mount the enclosure:
- inside a direct strike path for floating debris
- where service requires unsafe leaning into water
- on unstable rotten substrates
- where cable routing is constantly submerged without proper design
- where the sensor cannot maintain line-of-sight to the observed zone

---

# Recommended Default Build Profile

For the first serious Channel / Outfall Sentinel Node proof of concept, the strongest practical build profile is:

## Controller
- ESP32-class board

## Logging
- microSD + RTC

## Primary Sensor
- outdoor-capable radar or waterproof non-contact level sensor

## Secondary Sensor
- sealed threshold switch

## Local Status
- sunlight-visible LED or compact beacon

## Communications
- LoRa-capable module or board

## Power
- LiFePO4 battery + solar + charge controller + low-voltage protection

## Enclosure
- IP-rated UV-stable weather-resistant box with cable glands

## Mounting
- corrosion-resistant bracketed external mount with adjustable sensor aiming

This is the cleanest balance of:
- exposed-environment realism
- field survivability
- reproducibility
- trustworthy logs
- believable corridor-level value

---

# Critical Components Checklist

The Sentinel Node should not advance to exposed field pilot without all Class A items present and verified.

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
- sensor aiming hardware

## Class B — Strongly Important
- RTC
- secondary threshold sensor
- communications module
- antenna
- temperature/humidity sensor
- surge protection
- service labels
- sensor hood or splash guard

## Class C — Helpful but Optional
- buzzer
- optional camera
- bird/debris guard
- external level reference marker
- vibration isolation pads

---

# Suggested Spare Parts for Pilot Deployment

A serious exposed-node pilot should not rely on one copy of everything.

Recommended spares include:

- 1 spare primary sensor
- 1 spare secondary threshold sensor
- 1 spare controller board
- 1 spare SD card
- spare antenna
- spare cable glands
- spare fuses
- spare fasteners
- spare mounting hardware
- spare labeled connector set
- spare short cable harnesses

Exposed placements create harsh learning conditions. Spare parts are part of the pilot plan, not an afterthought.

---

# Assembly Dependencies

This BOM depends on additional files that should follow later in the repository:

- Sentinel Node assembly walkthrough
- Sentinel Node wiring guide
- Sentinel Node maintenance checklist
- node status schema
- event log schema
- proof-of-concept test checklist

The BOM alone is not enough for a serious build.

---

# Builder Notes

## For Early Builders
Start with:
- bench power
- no camera
- simple non-contact level sensing
- no solar until power budget is understood
- short-range communications during early development
- controlled outdoor dry run before storm exposure

Then harden deliberately.

## For Serious Field Pilot Builders
Use:
- real enclosure
- real bracket and sensor mount
- real local logs
- battery-backed power
- clear site labeling
- one primary sensor plus one secondary threshold path
- documented mount geometry
- service notes from day one

---

# Known Limitations of This BOM

This proof-of-concept BOM does not yet include:

- final region-specific part numbers
- final wiring harness drawings
- final enclosure cutout drawings
- final mount drawings
- final firmware state mapping
- final threshold values
- final debris-camera logic
- final backflow inference model
- certified lightning protection design
- long-term marine hardening package

That is intentional.

This BOM is the first believable exposed-environment step, not the finished end state.

---

# BOM Acceptance Criteria

This BOM should be considered usable only if the builder can answer yes to all of the following:

- Can I identify each subsystem clearly?
- Can I tell which parts are mission critical?
- Can I understand the preferred build path?
- Can I see which items are optional versus necessary?
- Can I build a real exposed-environment pilot from this list with the later assembly guide?
- Can I avoid making claims this build does not support?

If the answer is yes, the BOM is doing its job.

---

# Summary

This Channel / Outfall Sentinel Node proof-of-concept BOM is designed to create a **credible exposed-environment field node** for IX-Bayanihan.

It is meant to be:

- open
- modular
- serviceable
- field-aware
- honest
- rugged enough for pilot exposure
- expandable toward hardened deployment

Its role is simple but important:

> **Show broader flood-corridor and discharge conditions clearly enough to improve understanding of rising downstream pressure, backflow risk, exposed corridor behavior, and the relationship between local street flooding and larger drainage conditions.**

That is a serious and useful second proof-of-concept module.
