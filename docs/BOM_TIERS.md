# IX-Bayanihan BOM Tiers

## Purpose

This document defines the bill-of-materials strategy for **IX-Bayanihan**.

The goal is not to produce one giant shopping list that only wealthy teams can use.

The goal is to provide a **tiered hardware pathway** so that builders can start small, prove value, and scale upward based on local flood risk, budget, skills, and deployment needs.

The BOM strategy is organized into practical deployment tiers.

Each tier is designed to answer a different question:

- Can we build a useful local proof of concept with simple parts?
- Can we deploy a rugged pilot in a real flood-prone area?
- Can we harden the system for repeated community use?
- Can we prepare a serious district-facing architecture that supports public-interest deployment?

---

## Tier Philosophy

IX-Bayanihan uses BOM tiers because flood environments are not uniform.

A low-cost neighborhood pilot and a hardened estero-edge node do not need the same parts, the same enclosure, or the same power budget.

The tier system is used to avoid three common mistakes:

1. **Overbuilding too early**
2. **Underbuilding for harsh field conditions**
3. **Mixing prototype parts with operational claims**

Each tier has a different purpose, risk level, and expected service life.

---

## Tier Summary

IX-Bayanihan uses four BOM tiers.

### Tier 1 — Bench and Classroom Proof of Concept
Used for indoor demonstration, breadboard validation, firmware bring-up, sensor testing, and early logic verification.

### Tier 2 — Field Pilot Node
Used for short-duration outdoor pilot deployments in real flood-prone conditions with moderate hardening.

### Tier 3 — Hardened Community Node
Used for repeated outdoor deployment in harsh urban flood conditions with stronger enclosure, mounting, serviceability, and electrical protection.

### Tier 4 — District Integration Reference
Used as a reference architecture for multi-node deployments, gateways, expanded telemetry, stronger maintenance practices, and integration with wider operational systems.

---

## Important Scope Boundary

These BOM tiers do **not** represent:

- stamped engineering packages
- guaranteed code-compliant designs
- final procurement approval
- universal price certainty
- one-size-fits-all local legality
- a replacement for local environmental review
- a replacement for electrical or structural design authority

These tiers are open, practical build pathways intended to make the repository understandable and reproducible.

---

# Tier 1 — Bench and Classroom Proof of Concept

## Tier 1 Goal

Tier 1 exists to answer a simple question:

> Can the sensing, logging, thresholding, and alert logic work at all under controlled conditions?

Tier 1 is for learning, debugging, and proof of concept.

It is not for making outdoor durability claims.

## Tier 1 Typical Uses

- indoor firmware development
- threshold testing
- simulated water-rise testing
- simple enclosure fit checks
- LED or buzzer warning validation
- basic data logging verification
- classroom or workshop demonstration
- sensor comparison studies

## Tier 1 Recommended Characteristics

- low cost
- easy to source
- easy to replace
- easy to wire
- non-destructive to modify
- tolerant of mistakes
- simple to power from USB or bench supply

## Tier 1 Example BOM Categories

### Controller
- ESP32 development board or equivalent
- USB serial programming support
- onboard power indicator

### Water-Level Sensing
One of:
- waterproof ultrasonic sensor
- simple pressure sensor with test column
- non-contact water-level test sensor
- float switch for threshold-only experiments

### Local Alerting
- LED module
- piezo buzzer
- optional small indicator display

### Logging and Timekeeping
- microSD card module or equivalent local logging
- optional RTC module if needed

### Power
- USB power
- bench supply
- basic battery holder for demonstration only

### Wiring and Prototyping
- breadboard
- jumper wires
- terminal adapters
- simple resistors and protection parts

### Mechanical
- small prototype box
- cable glands for practice
- simple brackets or 3D-printed holders

## Tier 1 Strengths

- fastest route to proof of concept
- cheapest route to logic validation
- best for rapid iteration
- easy for contributors to reproduce

## Tier 1 Weaknesses

- poor environmental durability
- weak long-term sealing
- limited surge protection
- not fit for dirty urban drainage deployment
- not fit for harsh UV, sediment, trash, or biofouling exposure

## Tier 1 Exit Criteria

A Tier 1 design is ready to advance only when it can demonstrate:

- stable boot and recovery behavior
- repeated sensor reads without obvious instability
- basic threshold transition logic
- event logging
- local alert output
- basic degraded-mode handling
- clear assembly documentation

---

# Tier 2 — Field Pilot Node

## Tier 2 Goal

Tier 2 exists to answer:

> Can the design survive real short-term flood-prone outdoor deployment and produce useful data?

Tier 2 is where IX-Bayanihan becomes a field project rather than just a bench exercise.

## Tier 2 Typical Uses

- pilot deployment at a flood-prone curb inlet
- pilot deployment at an underpass or sump edge
- pilot deployment near a drainage channel
- first real serviceability test
- first real debris exposure test
- real communications trial
- real battery endurance trial
- first maintenance-interval assessment

## Tier 2 Recommended Characteristics

- weather-resistant enclosure
- replaceable sensors
- modest surge protection
- battery-backed operation
- outdoor-safe cable routing
- mounting method suitable for real infrastructure
- local service labeling

## Tier 2 Example BOM Categories

### Controller
- ESP32, STM32, RP2040-based industrial-capable controller, or equivalent
- watchdog support
- nonvolatile event storage

### Water and Condition Sensing
Possible combinations:
- waterproof ultrasonic or radar level sensor
- pressure transducer in protected tube or chamber
- float switch as a secondary threshold fail-safe
- temperature and enclosure humidity sensor
- optional tilt or tamper sensor

### Clog / Blockage Awareness
One or more of:
- paired water-level differential interpretation
- pressure differential interpretation
- optical interruption check inside protected intake path
- motor current sensing for self-cleaning accessory
- persistent ponding timer logic

### Local Alerting
- visible high-brightness LED
- local buzzer where context-appropriate
- service-needed indicator

### Logging
- onboard flash or removable local storage
- timestamped event record
- fault history ring buffer

### Communications
One or more of:
- LoRa
- LoRaWAN
- LTE/4G module
- Wi-Fi for pilot areas with known access
- short-range relay radio

### Power
- small solar panel where exposure is realistic
- LiFePO4 battery
- charge controller
- fuse
- reverse-polarity protection
- TVS diode or equivalent transient protection

### Enclosure and Mounting
- IP-rated enclosure appropriate for splash and rain exposure
- cable glands
- stainless fasteners where possible
- pipe clamp, wall bracket, or curbside anchor hardware
- service label plate

## Tier 2 Strengths

- real-world validation
- meaningful telemetry testing
- early maintenance learning
- practical deployment evidence
- realistic power endurance data

## Tier 2 Weaknesses

- still vulnerable to extreme debris load
- still vulnerable to theft or vandalism if not well mounted
- may require frequent service in dirty environments
- not yet ideal for long unattended deployment

## Tier 2 Exit Criteria

Tier 2 is ready to advance when it demonstrates:

- stable outdoor operation over repeated weather cycles
- useful data from real flood-prone placement
- credible local sealing
- service access without destructive disassembly
- successful recovery after temporary comms loss
- battery behavior consistent with design expectations
- clear maintenance observations from real use

---

# Tier 3 — Hardened Community Node

## Tier 3 Goal

Tier 3 exists to answer:

> Can the design be deployed repeatedly in harsh community flood conditions with strong serviceability and credible resilience?

Tier 3 is the first tier that should feel operational rather than experimental.

## Tier 3 Typical Uses

- repeated seasonal deployment in known flood hotspots
- curb inlet or underpass monitoring in dirty urban conditions
- estero or outfall-edge monitoring with strong enclosure requirements
- community-maintained neighborhood flood node
- NGO or municipal demonstration site
- protected pump-approach observation node

## Tier 3 Recommended Characteristics

- rugged enclosure
- corrosion-resistant hardware
- protected sensor placement
- stronger cable strain relief
- replaceable power subsystem
- stronger local diagnostics
- better physical service access
- visible maintenance tagging
- more disciplined fault isolation

## Tier 3 Example BOM Categories

### Controller
- industrial or semi-industrial microcontroller platform
- watchdog and brownout handling
- fault-state persistence
- versioned firmware identification
- optional dual-partition firmware update capability

### Water and Condition Sensing
Preferred combinations:
- industrial waterproof radar or ultrasonic level sensor
- protected pressure transducer in serviceable chamber
- float switch or secondary threshold channel
- enclosure temperature and humidity sensing
- door-open or tamper switch
- optional debris-facing camera in protected viewport

### Clog / Blockage Awareness
Possible combinations:
- dual-point level comparison
- intake persistence logic
- differential pressure sensing across screen or path
- self-cleaning actuator position sensing
- camera-assisted blockage inference
- maintenance lockout recognition

### Local Alerting
- sealed high-visibility beacon
- service indicator
- optional local siren only if appropriate to community context
- QR or printed service label for field crew lookup

### Logging and Evidence
- event log with fault codes
- local storage with write-failure handling
- maintenance log import pathway
- last-good-state snapshot
- offline logging mode

### Communications
One or more of:
- LoRa / LoRaWAN primary
- cellular secondary
- gateway aggregation support
- delayed sync and store-and-forward logic
- local debug port protected behind service access

### Power
- solar + LiFePO4 + power management board
- supercapacitor buffer where justified
- fuse and resettable protection as appropriate
- surge protection
- low-voltage disconnect
- protected charging path
- battery service connector

### Enclosure and Mounting
- UV-stable enclosure
- corrosion-resistant external hardware
- stainless or coated mount hardware
- anti-vibration mounting
- tamper-resistant fasteners where needed
- replaceable sacrificial sensor shield or splash guard
- sediment-aware mounting offset

## Tier 3 Strengths

- credible community deployment pathway
- better long-term resilience
- stronger maintenance discipline
- stronger visibility for operators and crews
- more believable proof of public usefulness

## Tier 3 Weaknesses

- higher cost
- more complex service procedures
- more demanding sourcing
- higher burden of documentation
- greater responsibility to define safe installation procedures

## Tier 3 Exit Criteria

A Tier 3 design should demonstrate:

- repeated survivability in harsh outdoor conditions
- maintainable enclosure access
- recoverable operation after faults
- useful data during real deteriorating conditions
- clear maintenance interval recommendations
- replaceable and labeled subassemblies
- evidence that the system helps identify practical flood pain points earlier than manual observation alone

---

# Tier 4 — District Integration Reference

## Tier 4 Goal

Tier 4 is not one single hardware unit.

It is a **reference deployment architecture** for scaling IX-Bayanihan across a neighborhood, corridor, or district.

Tier 4 exists to answer:

> How do multiple nodes, gateways, logs, and operational interfaces work together in a coherent flood-support deployment?

## Tier 4 Typical Uses

- cluster deployments
- street + channel combined pilot
- gateway and relay testing
- operator dashboard integration
- maintenance fleet workflow testing
- district flood hotspot analysis
- future integration planning with pumps, gates, or wider municipal systems

## Tier 4 Recommended Characteristics

- multiple node classes
- gateway or relay support
- consistent data schema
- event dashboard
- maintenance tracking pathway
- node version tracking
- service history by asset
- documented deployment topology

## Tier 4 Example BOM Categories

### Field Node Set
- multiple Tier 2 or Tier 3 street nodes
- multiple channel or outfall nodes
- optional beacon nodes
- optional relay nodes

### Gateway / Aggregation Hardware
- industrial edge computer or rugged single-board computer
- protected power input
- local storage
- multi-radio support where needed
- enclosure appropriate to sheltered infrastructure placement

### Operations Layer
- dashboard workstation or edge UI
- event store
- node registry
- severity scoring logic
- maintenance record database or flat-file equivalent
- exportable logs

### Communications Backbone
- local radio topology
- gateway uplink
- fallback logging behavior
- health-check heartbeat logic
- communications fault alerting

### Power Continuity
- protected site power
- backup battery or UPS for gateway
- surge protection
- power-fault reporting

## Tier 4 Strengths

- realistic systems view
- stronger operational believability
- useful for NGOs, municipalities, researchers, and public-interest implementers
- capable of showing system-level value instead of single-node novelty

## Tier 4 Weaknesses

- not a simple hobby build
- requires stronger documentation discipline
- requires clearer role separation between field gear and operations software
- requires better data hygiene and maintenance practice

## Tier 4 Success Criteria

Tier 4 is successful if it can demonstrate:

- multiple active nodes with coherent state reporting
- useful operator-level summary of flood conditions
- reliable maintenance-needed visibility
- useful identification of recurring choke points
- evidence that a network provides more value than isolated nodes

---

# BOM Strategy by Node Class

IX-Bayanihan BOMs will eventually be organized by node class.

## Node Class A — Smart Inlet Node
Designed for:
- curb inlets
- roadside drains
- small sumps
- alley flood points

Likely BOM emphasis:
- compact enclosure
- low-cost level sensing
- blockage inference
- local service access
- low-power operation

## Node Class B — Underpass or Hazard Depth Node
Designed for:
- underpasses
- low road cuts
- enclosed low points
- hazardous standing-water corridors

Likely BOM emphasis:
- stronger local alerting
- protected sensor placement
- clearer threshold logic
- more visible beaconing

## Node Class C — Estero / Channel Sentinel Node
Designed for:
- drainage channels
- esteros
- canal edges
- river-adjacent drainage points

Likely BOM emphasis:
- stronger enclosure
- corrosion resistance
- long-range telemetry
- water-level trend sensing
- optional camera support

## Node Class D — Outfall / Backflow Node
Designed for:
- outfalls
- tidal interfaces
- backflow-prone locations
- drainage discharge edges

Likely BOM emphasis:
- water level and downstream condition awareness
- strong environmental hardening
- mounting against splash, sediment, and corrosive exposure

## Node Class E — Gateway Node
Designed for:
- field aggregation
- relay support
- dashboard uplink

Likely BOM emphasis:
- more compute
- more power continuity
- more protected installation
- stronger local storage

---

# BOM Cost Posture

IX-Bayanihan should avoid pretending that one budget works everywhere.

Instead, BOMs should be described using cost posture language:

- **low-cost**
- **moderate-cost**
- **hardened**
- **district-reference**

This is more honest than fake universal pricing because component costs change by region, time, taxes, shipping, import conditions, and availability.

When specific examples are listed later, they should be treated as **reference examples**, not guaranteed prices.

---

# Sourcing Doctrine

Future BOM files in this repository should follow these sourcing rules:

1. Prefer parts with multiple equivalent suppliers where possible.
2. Avoid rare single-source parts unless there is a strong reason.
3. Prefer parts that can survive replacement cycles.
4. Prefer standard fasteners, connectors, and cable hardware.
5. Label which parts are mission-critical and which are optional.
6. Separate prototype parts from hardened deployment parts.
7. Call out any part that demands special handling, calibration, sealing, or licensing.

---

# BOM Structure Standard

Each future BOM in IX-Bayanihan should include these fields.

## Required BOM Fields

- item number
- subsystem
- part description
- function
- quantity
- preferred specification
- acceptable alternatives
- deployment tier
- notes
- criticality class

## Optional but Recommended Fields

- approximate power draw
- environmental notes
- mounting notes
- sealing notes
- maintenance notes
- local sourcing notes
- calibration notes
- known failure modes

---

# Criticality Classes

To improve clarity, each major component should be tagged with a criticality class.

## Class A — Mission Critical
Failure prevents the node from serving its primary purpose.

Examples:
- controller
- primary sensor
- battery
- power regulation path

## Class B — Strongly Important
Failure reduces node usefulness significantly but may not fully disable it.

Examples:
- communications module
- secondary sensor
- local beacon
- environmental monitor

## Class C — Helpful but Optional
Failure does not destroy core node function.

Examples:
- local display
- auxiliary camera
- decorative enclosure labels
- nonessential comfort diagnostics

This helps contributors understand what can be downgraded when budgets are tight.

---

# Build Progression Recommendation

The recommended order for builders is:

1. Tier 1 bench proof of concept
2. Tier 2 short-term field pilot
3. Tier 3 hardened community node
4. Tier 4 district integration reference

Skipping directly to a hardened deployment without a proof-of-concept phase increases the chance of hidden mistakes, poor serviceability, and wasted money.

---

# Documentation Standard for Each BOM

Every future node-specific BOM should be paired with:

- a wiring diagram
- an enclosure layout note
- a mounting note
- a power note
- a maintenance note
- a known-limitations note
- a short assembly guide
- a short test checklist

The BOM alone is never enough.

The BOM must be buildable.

---

# What the Tiers Mean in Practice

The tier labels are not cosmetic.

They tell the reader how much confidence they should place in the build.

## Tier 1 Means
"This works enough to prove the sensing and control idea."

## Tier 2 Means
"This works enough to test outdoors and learn from reality."

## Tier 3 Means
"This works enough to be taken seriously as a repeatable field asset."

## Tier 4 Means
"This works enough to support a broader deployment architecture and operations model."

---

# Success Standard for IX-Bayanihan BOMs

A good IX-Bayanihan BOM is:

- understandable
- realistic
- modular
- reproducible
- honest about limitations
- clearly tiered
- maintainable in the field
- compatible with the repository’s claim boundary

A bad IX-Bayanihan BOM is:

- vague
- magical
- impossible to source
- impossible to assemble
- impossible to maintain
- overclaimed
- missing alternatives
- disconnected from real deployment conditions

---

# Summary

IX-Bayanihan uses a tiered BOM system so that builders can:

- start small
- validate honestly
- harden responsibly
- scale deliberately

The tier system is part of the project’s discipline.

It helps keep the repository practical, believable, and useful.

Future files in this repository will build on this tier model to provide:

- node-specific BOMs
- proof-of-concept part lists
- hardened deployment variants
- gateway and operations hardware references
- assembly walkthroughs tied directly to the correct deployment tier
