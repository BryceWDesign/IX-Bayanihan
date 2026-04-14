# IX-Bayanihan Proof-of-Concept Module Specifications

## Purpose

This document defines the three core proof-of-concept modules for **IX-Bayanihan**.

These modules are the minimum viable architecture required to demonstrate that the project can provide useful flood-support value in the real world.

The three modules are:

1. **Smart Inlet Node**
2. **Channel / Outfall Sentinel Node**
3. **Local Flood Operations Console**

Together, they create a coherent small-scale flood-support system with:

- street-level sensing
- corridor-level sensing
- local visibility
- event logging
- degraded-mode behavior
- operational interpretation

This document describes what each module is supposed to do, what it must contain, what it must not pretend to do, and what design expectations apply.

---

## Why These Modules Exist

The proof of concept needs to demonstrate more than one isolated sensor.

A single sensor can show that a part works.

A three-module stack can show that a **system** works.

That difference matters.

IX-Bayanihan needs to prove that:

- local flood conditions can be sensed
- broader hydraulic context can be sensed
- useful interpretation can be preserved
- maintenance and fault signals can be surfaced clearly

That is why the proof of concept is built around these three module classes.

---

# Module 1 — Smart Inlet Node

## Role

The Smart Inlet Node is the **street-facing module**.

It is designed to observe local drainage trouble points where flood harm often becomes visible first.

Typical locations include:

- curb inlets
- roadside drains
- shallow sumps
- alley drains
- low roadside depressions
- underpass approach drains
- stairwell-adjacent drains
- roadside collection pockets

The Smart Inlet Node should be the first module to show that a neighborhood-scale flood-support system is practical.

---

## Primary Mission

The Smart Inlet Node exists to answer these questions:

- Is water rising near the drain or inlet?
- Is the rise persistent instead of clearing normally?
- Is the drain likely blocked, overloaded, or backing up?
- Is the node still healthy enough to trust?
- Does this location need cleaning, inspection, or escalation?

---

## Core Functional Requirements

The Smart Inlet Node should provide the following minimum functions.

### 1. Water-Level Awareness
The node must sense water presence or water depth trend near the monitored drain or inlet.

### 2. Threshold State Logic
The node must support at least these states:

- NORMAL
- WATCH
- ALERT
- DEGRADED
- FAULT

### 3. Local Visible Status
The node must provide some simple local status indication that survives loss of centralized monitoring.

### 4. Event Logging
The node must record threshold crossings, faults, and significant state transitions.

### 5. Maintenance Flagging
The node should provide some way to indicate when a location appears to need service, cleaning, or inspection.

### 6. Power-State Visibility
The node must track whether it is healthy, low on power, unstable, or unable to continue normal operation.

### 7. Graceful Degradation
If communication or a sensor input is lost, the node should continue doing as much of its job as possible without pretending all is normal.

---

## What the Smart Inlet Node Must Not Claim

The Smart Inlet Node must not claim to:

- fully diagnose every blockage type
- measure full hydraulic capacity of a drainage network
- replace a professional inspection
- guarantee that a drain will or will not fail
- prove city-scale flood performance from one placement
- make drainage conditions magically visible when the sensor is poorly placed

The node is a practical field instrument, not a miracle object.

---

## Recommended Sensing Strategy

The Smart Inlet Node should prefer simple, robust sensing combinations.

Possible useful sensing combinations include:

- one primary water-level sensor plus one secondary threshold sensor
- one water-level sensor plus persistent ponding timer logic
- one water-level sensor plus enclosure health sensing
- one water-level sensor plus optional blockage inference signal

The system should avoid relying entirely on a single magical interpretation path.

---

## Suggested Inputs

The Smart Inlet Node may include some subset of the following inputs.

### Required or Near-Required Inputs
- water-level signal
- power-state signal
- controller health signal

### Strongly Recommended Inputs
- enclosure temperature and humidity
- low-voltage status
- local communications health
- service/reset input

### Optional Inputs
- clog inference input
- screen differential signal
- tilt or tamper signal
- local debris-view camera
- rain context input if available nearby

Not every build must include every input, but the module design should make the roles clear.

---

## Suggested Outputs

The Smart Inlet Node should support some subset of these outputs.

### Minimum Outputs
- local state indicator
- local event log
- heartbeat or health report
- fault report
- maintenance-needed flag

### Optional Outputs
- local buzzer
- visible high-water beacon
- QR or label reference for maintenance crews
- relay output for local auxiliary indicator

The module should remain understandable even with minimal outputs.

---

## Smart Inlet Node Physical Design Priorities

The physical design should prioritize:

- compact form factor
- dirty-water tolerance
- easy mounting
- easy enclosure access
- replaceable sensing path
- protected cable routing
- clear service label visibility
- ordinary tool access for maintenance

The first design should not be beautiful at the expense of survivability.

---

## Smart Inlet Node Environmental Risks

The Smart Inlet Node should be designed with these failure pressures in mind:

- trash accumulation
- leaf and sediment build-up
- splash and standing water
- vibration from road traffic
- heat and humidity cycling
- cable strain
- enclosure leaks
- bio-growth
- vandalism or accidental impact

Any design that ignores these factors is not ready for real flood-prone deployment.

---

## Smart Inlet Node Success Signals

A Smart Inlet Node is doing useful work if it can consistently show:

- rising water before dangerous ponding becomes obvious
- persistent water that should have drained faster
- repeat trouble at the same inlet over multiple rain events
- clear difference between normal and concerning conditions
- clear indication when the node itself is unhealthy

That is enough to be genuinely useful.

---

# Module 2 — Channel / Outfall Sentinel Node

## Role

The Channel / Outfall Sentinel Node is the **corridor-facing module**.

It monitors broader drainage behavior at exposed locations that influence neighborhood flood performance.

Typical locations include:

- esteros
- channels
- culvert mouths
- drainage canals
- river-adjacent drain corridors
- outfalls
- tidal interfaces
- backflow-prone discharge points
- pump approach water corridors

This node is not a drain accessory.
It is a broader-context observation point.

---

## Primary Mission

The Channel / Outfall Sentinel Node exists to answer these questions:

- Is downstream water already too high for drainage to work well?
- Is the broader channel rising faster than expected?
- Is backflow likely or already occurring?
- Is debris loading becoming dangerous?
- Is the corridor condition helping explain local street flooding?
- Can this exposed point remain visible to operators during a storm?

---

## Core Functional Requirements

The Channel / Outfall Sentinel Node should provide the following minimum functions.

### 1. Water-Level Trend Sensing
The node must track changing water conditions over time, not just a single threshold crossing.

### 2. Broader Context Visibility
The node must provide information that complements the street node rather than duplicates it.

### 3. Event Logging
The node must record changing hydraulic conditions, health events, and communications disruptions.

### 4. Communications Persistence
The node should favor strong telemetry continuity or strong offline logging in case uplink is unstable.

### 5. Exposed-Environment Survivability
The node must be designed for dirtier, wetter, more exposed placement than the Smart Inlet Node.

### 6. Degraded-Mode Discipline
The node must show when it remains useful and when it should not be trusted.

---

## What the Sentinel Node Must Not Claim

The Channel / Outfall Sentinel Node must not claim to:

- replace a full hydrologic or hydraulic model
- provide guaranteed storm-surge prediction
- provide legal flood warnings on behalf of authorities
- diagnose every cause of channel rise
- replace basin-wide instrumentation or public flood networks

It is a context node, not a full river authority.

---

## Recommended Sensing Strategy

The Sentinel Node should prefer robust, low-maintenance sensing with protected mechanical placement.

Possible useful sensing strategies include:

- water-level sensor with trend and persistence logic
- water-level sensor with secondary threshold sensor
- water-level sensor with enclosure health and power monitoring
- optional debris observation aid
- optional local camera or visibility aid where lawful and practical

The design should prefer sensors that remain useful in muddy, splash-heavy, dirty environments.

---

## Suggested Inputs

The Channel / Outfall Sentinel Node may include:

### Required or Near-Required Inputs
- water-level signal
- controller health
- power state

### Strongly Recommended Inputs
- communication health
- enclosure humidity
- local temperature
- installation orientation or tamper awareness

### Optional Inputs
- downstream/backflow inference input
- current or wave motion context
- camera input
- debris or occlusion indicator
- rain context from nearby nodes or gateway

---

## Suggested Outputs

The Sentinel Node should support some subset of:

### Minimum Outputs
- water-condition state
- heartbeat
- power state
- event log
- fault or degraded state

### Optional Outputs
- local beacon
- camera snapshot trigger
- relay support for nearby lower-power nodes
- downstream condition summary flag

The core output should remain simple enough that field teams can interpret it.

---

## Sentinel Node Physical Design Priorities

The Sentinel Node should prioritize:

- corrosion resistance
- stable mounting
- splash and immersion protection appropriate to deployment
- longer communications reach
- safer service access
- more visible labeling
- more durable cable sealing
- optional anti-fouling considerations where practical

This node is a harsher-environment asset and should be treated as such.

---

## Sentinel Node Environmental Risks

The Sentinel Node must expect:

- stronger splash loads
- longer wet periods
- debris strikes
- corrosion
- biofouling
- sediment deposition
- difficult maintenance approach
- radio obstruction
- unstable mounting surface
- high winds or weather exposure

A casual enclosure is not enough here.

---

## Sentinel Node Success Signals

A Channel / Outfall Sentinel Node is doing useful work if it can consistently show:

- broader water rise before local flooding worsens
- recurring downstream conditions that correlate with local drainage failure
- visible exposure of outfall submergence or backflow risk
- useful logs even when communications are intermittent
- a clear difference between flood-related change and hardware decline

That makes it valuable.

---

# Module 3 — Local Flood Operations Console

## Role

The Local Flood Operations Console is the **interpretation and visibility module**.

It is the place where field node states are collected, summarized, and made understandable.

This module may be:

- a lightweight dashboard
- a local laptop tool
- a small edge UI
- a simple browser-based interface
- a low-complexity monitoring panel

The key requirement is that it remains practical and understandable.

---

## Primary Mission

The Local Flood Operations Console exists to answer these questions:

- Which nodes are normal?
- Which nodes are in watch or alert?
- Which nodes are degraded or faulty?
- What changed recently?
- Which sites need inspection first?
- Which nodes have gone silent?
- Is the event worsening, stabilizing, or recovering?

This module turns raw node behavior into actionable situational awareness.

---

## Core Functional Requirements

The Local Flood Operations Console should provide the following minimum functions.

### 1. Node State Visibility
Show the current state of each node in a clear and fast-to-read way.

### 2. Last-Seen Visibility
Show whether nodes are still reporting or may have gone offline.

### 3. Event History
Allow review of recent state transitions and meaningful logged events.

### 4. Fault Separation
Distinguish flood-condition alerts from hardware faults or degraded sensing.

### 5. Maintenance Awareness
Show which nodes are likely requesting service, cleaning, or inspection.

### 6. Simple Severity Framing
Provide an understandable indication of which points are the most concerning right now.

---

## What the Console Must Not Claim

The Local Flood Operations Console must not pretend to be:

- a city emergency command center
- a life-safety certified warning platform
- an official government flood forecast system
- a complete hydrologic modeling environment
- a replacement for human judgment

The first proof of concept should stay simple and honest.

---

## Minimum Information the Console Should Display

The console should show at least the following for each node:

- node identifier
- node class
- current state
- last seen time
- water or trend status
- power health
- communication health
- fault state
- maintenance-needed flag

Optional display features can be added later, but these are the minimum.

---

## Recommended Console Views

The first version should remain simple and focused.

Useful views include:

### 1. Node Summary View
A list of all nodes with current state and last-seen information.

### 2. Event History View
A recent chronological list of changes, alerts, and faults.

### 3. Maintenance View
A list of nodes that likely need inspection, cleaning, or service.

### 4. Site Detail View
A simple per-node page or panel showing recent history and health indicators.

That is enough for a believable first console.

---

## Recommended Severity Framing

The console should not use vague drama language.

It should use clear system states such as:

- NORMAL
- WATCH
- ALERT
- DEGRADED
- FAULT
- OFFLINE_LOGGING

Optionally, it may support roll-up severity levels for operator convenience, such as:

- low concern
- rising concern
- active concern
- service concern

But the underlying node states should remain explicit.

---

## Console Data Expectations

The console should expect that field data is imperfect.

It must gracefully handle:

- late packets
- missing packets
- duplicate packets
- nodes that temporarily disappear
- stale values
- nodes stuck in degraded mode
- clocks that are not perfectly aligned in early prototypes

The console should prefer clarity over false precision.

---

## Console Success Signals

A Local Flood Operations Console is doing useful work if it can consistently help a user answer:

- what is happening
- where it is happening
- what changed recently
- whether the node is trustworthy
- what should be inspected first

If a user cannot answer those questions quickly, the console is too weak or too noisy.

---

# How the Three Modules Work Together

The proof-of-concept modules are designed to reinforce one another.

## Smart Inlet Node Contribution
Shows local street or drain failure onset.

## Sentinel Node Contribution
Shows whether the broader corridor or outfall condition may be driving or worsening that local failure.

## Operations Console Contribution
Shows all nodes together in a way that supports action, comparison, and post-event understanding.

This three-part structure is the minimum coherent IX-Bayanihan system.

---

## Example Interpretive Patterns

The modules should make patterns like these visible.

### Pattern A — Local Drain Trouble
- Smart Inlet Node enters WATCH and ALERT
- Sentinel Node remains normal
- likely interpretation: local blockage, local overload, or local drainage problem

### Pattern B — Broader Downstream Problem
- Sentinel Node rises first
- nearby Smart Inlet Node later enters WATCH
- likely interpretation: downstream or corridor condition is reducing drainage performance

### Pattern C — Node Hardware Trouble
- node reports low power, bad sensor health, or stale reads
- console marks DEGRADED or FAULT
- likely interpretation: service needed before trusting the readings

### Pattern D — Recovering Event
- Sentinel Node trend falls
- Smart Inlet Node returns from ALERT to WATCH to NORMAL
- likely interpretation: drainage recovery in progress

These kinds of visible patterns are what make the architecture useful.

---

## Initial Revision Priorities for All Modules

The first revision cycle after the proof of concept should focus on:

- simpler field service
- stronger enclosure reliability
- clearer local indicators
- cleaner fault reporting
- better power recovery behavior
- more reliable logging
- fewer ambiguous states
- stronger maintenance labeling

The first proof of concept should not chase too many fancy features too early.

---

## Cross-Module Design Rules

All three modules should follow these common rules.

### Rule 1
Every module must fail visibly when possible.

### Rule 2
Every module must preserve evidence of important state changes.

### Rule 3
Every module must distinguish "bad environment" from "bad hardware" as clearly as possible.

### Rule 4
Every module must be understandable by a disciplined builder or field operator.

### Rule 5
Every module must be documented well enough that another person can reproduce it.

---

## Proof-of-Concept Module Boundary Statement

The proof-of-concept module set is intended to prove that IX-Bayanihan can function as a useful flood-support stack at small scale.

It is not intended to claim that:

- a single deployment solves flood risk
- a small prototype replaces infrastructure
- a dashboard equals flood control
- a sensor alone equals flood safety

The point is disciplined demonstration.

That is enough.

---

## Summary

The three proof-of-concept modules for IX-Bayanihan are:

1. **Smart Inlet Node**
2. **Channel / Outfall Sentinel Node**
3. **Local Flood Operations Console**

These modules provide the minimum architecture needed to show that the project can deliver:

- local visibility
- broader drainage context
- understandable operations support

That is the correct starting point for a serious, open, humanitarian flood-resilience repository.
