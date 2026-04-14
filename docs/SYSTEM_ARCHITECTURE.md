# IX-Bayanihan System Architecture

## Architecture Intent

IX-Bayanihan is structured as a **layered flood-resilience system** made of modular field hardware, resilient local control, telemetry, and operator-facing decision support.

The architecture is designed to improve outcomes in flood-prone environments by making it easier to:

- observe rising water sooner
- detect drainage failure earlier
- recognize debris and blockage conditions faster
- preserve visibility during outages or degraded conditions
- support safer response decisions
- scale from small pilot deployments to larger district-level networks

This repository is built around the assumption that many damaging flood events become worse because field conditions are not visible, blockages are discovered too late, and infrastructure state is poorly understood during the event.

---

## High-Level System Model

IX-Bayanihan is organized into five main layers:

1. **Street and Inlet Layer**  
   Smart local nodes placed at drains, curb inlets, sumps, underpasses, and low points.

2. **Channel and Outfall Layer**  
   Monitoring nodes placed at esteros, canals, outfalls, tidal interfaces, culverts, and river-adjacent drainage corridors.

3. **Power and Communications Layer**  
   Resilient electrical and telemetry support for keeping useful information alive during unstable conditions.

4. **Flood Operations Layer**  
   Thresholding, logging, evidence capture, alert generation, degraded-mode control, and future pump/gate coordination support.

5. **Field Deployment and Maintenance Layer**  
   Installation, inspection, service intervals, cleaning routines, and replacement pathways for hardware in harsh real-world conditions.

Each layer is useful on its own, but the architecture becomes significantly more valuable when the layers are connected.

---

## Primary Architecture Goal

The system is designed to answer these practical questions during a flood event:

- Is water rising faster than expected?
- Which drains or inlets are failing first?
- Where is debris likely blocking flow?
- Is backflow occurring at the outfall or channel edge?
- Are the field nodes still alive and trustworthy?
- Which areas should be cleaned, inspected, or serviced first?
- Which signals are strong enough to justify warnings or operator action?
- Which parts of the system have degraded and entered safe mode?

---

## Core Design Principles

### 1. Modular Before Monolithic
The system is divided into modular units that can be deployed independently and upgraded over time.

### 2. Field Survivability First
A simple flood node that survives the storm is more valuable than a complex one that fails in the first harsh event.

### 3. Visibility Before Automation
Automation is useful, but visibility and trustworthy telemetry come first.

### 4. Degraded Mode Must Be Planned
Every major module must define how it behaves during sensor loss, low power, poor communications, or partial flooding.

### 5. Mechanical Reality Matters
Trash, sediment, corrosion, vibration, heat, humidity, and inaccessible service locations are primary design constraints.

### 6. Evidence Must Outlive the Event
Useful logs, fault state history, and event markers should remain available after the storm for review and improvement.

### 7. Layered Defense Beats One Big Device
The architecture is strongest when monitoring, protection, warning, drainage awareness, and operations support are stacked together.

---

## Architecture Layers in Detail

## Layer A: Street and Inlet Layer

This is the neighborhood-facing layer.

It is intended for places where flood harm begins locally:

- curb inlets
- roadside drains
- alleys
- low intersections
- underpasses
- sumps
- stairwell-adjacent drains
- street depressions
- culvert approaches

### Street Layer Functions

- local water level sensing
- rapid rise detection
- blocked inlet indication
- standing-water persistence detection
- local alert output
- telemetry uplink
- maintenance flagging
- service state recording

### Typical Street Layer Node Classes

#### A1. Smart Inlet Node
Installed directly at or beside a drain or curb inlet.

Core duties:
- detect water rise near the intake
- infer blockage risk
- detect persistent ponding
- report node health

#### A2. Smart Sump Node
Installed in small collection pits, sumps, or enclosed drainage pockets.

Core duties:
- sense rising water in confined drainage points
- detect pump inactivity or overload where applicable
- trigger local high-water state

#### A3. Underpass Flood Node
Installed at road underpasses or low enclosed vehicular corridors.

Core duties:
- detect hazardous depth conditions
- track rate of rise
- support warning thresholds

### Street Layer Architecture Requirements

Street-layer hardware should be:

- compact
- physically protected
- easy to replace
- low power
- weather sealed
- debris tolerant
- simple to mount and service
- understandable by field crews

---

## Layer B: Channel, Estero, Outfall, and Backflow Layer

This is the drainage-corridor-facing layer.

It focuses on points where broader hydraulic behavior affects neighborhoods:

- esteros
- canals
- outfalls
- culverts
- riverside drainage points
- tidal interfaces
- backflow-prone locations
- pump station approaches

### Channel Layer Functions

- water-level sensing
- outfall submergence awareness
- tidal backflow awareness
- channel rise trend tracking
- debris load awareness
- camera-assisted observation
- radio relay support
- local visible alerting where appropriate

### Typical Channel Layer Node Classes

#### B1. Estero Sentinel Node
Placed at small urban channels or esteros.

Core duties:
- monitor level changes
- identify repeated overflow conditions
- support debris observation
- maintain telemetry visibility during storms

#### B2. Outfall Backflow Node
Placed near outfalls or drain exits exposed to river, estuary, or tidal influence.

Core duties:
- detect when downstream levels are high enough to reduce drainage effectiveness
- identify possible backflow conditions
- support outfall-specific warnings

#### B3. Pump-Approach Monitoring Node
Placed upstream of pump inlets or around pump station inflow corridors.

Core duties:
- show approach water conditions
- infer debris loading risk
- provide independent verification of deteriorating inflow behavior

### Channel Layer Architecture Requirements

Channel-facing nodes should emphasize:

- corrosion resistance
- biofouling tolerance
- hardened mounting
- strong enclosure sealing
- visible service labeling
- stable communications pathways
- survivability in dirty water environments

---

## Layer C: Power and Communications Continuity Layer

Flood nodes are only useful if they remain alive long enough to produce meaningful information.

This layer provides the support needed to preserve operation during:

- unstable grid power
- battery stress
- low sunlight periods
- storm-induced outages
- intermittent communications
- field isolation

### Core Functions

- primary power conditioning
- battery management
- surge and reverse-polarity protection
- load shedding
- state-of-charge reporting
- local power fault recording
- communications failover
- time-stamped event preservation

### Design Intent

The continuity layer is not meant to power heavy municipal infrastructure like large pumps.

It is meant to keep:

- sensors alive
- controllers running
- local warning outputs available
- event logging intact
- telemetry active long enough to remain useful

### Communications Philosophy

The communications strategy should assume that no single link is always available.

The architecture should support combinations of:

- local storage
- delayed sync
- short-range relay
- cellular uplink where available
- alternative low-bandwidth fallback methods

Communication failure should reduce visibility, not erase the event history.

---

## Layer D: Flood Operations and Decision Layer

This is the logic and evidence layer.

It turns raw field signals into usable operational context.

### Core Functions

- threshold evaluation
- event classification
- degraded-mode handling
- node trust scoring
- state transitions
- warning trigger logic
- maintenance flag generation
- operator summary generation
- replayable event logging

### Flood Operations Duties

The operations layer should help answer:

- what changed
- where it changed
- how severe it looks
- whether the signal is trustworthy
- whether the situation is worsening
- what category of action is justified
- which field crews should be sent first
- whether a node has become unreliable

### Decision Support Boundaries

The operations layer is **decision support**, not autonomous citywide command authority.

It may support:
- warnings
- maintenance prioritization
- local intervention logic
- operator awareness
- future integration with controlled infrastructure

It does not replace licensed authority, emergency command, or formal engineering control packages.

---

## Layer E: Field Deployment and Maintenance Layer

This is the part many projects ignore and later regret.

Flood hardware does not fail only because of electronics.
It also fails because of:

- inaccessible installation points
- poor mounting
- bad service intervals
- unclear cleaning procedures
- weak cable routing
- corroded fasteners
- hidden clogging
- unlabeled replacement parts
- neglected inspection practice

### Core Duties

- installation guidance
- cleaning schedules
- inspection checklists
- part replacement guidance
- enclosure open/close procedures
- maintenance record structure
- failure tagging
- end-of-life handling

### Maintenance Doctrine

Every field module should be maintainable by a disciplined technician using ordinary tools whenever possible.

If a module requires unusually specialized conditions to stay operational, it is a poor fit for this repository.

---

## Node Taxonomy

IX-Bayanihan uses a node-based architecture.

### Node Categories

#### 1. Street Nodes
Used for local flood onset and inlet failure awareness.

#### 2. Channel Nodes
Used for open-water corridor and outfall awareness.

#### 3. Sentinel Nodes
Used for persistent observation in exposed, strategic, or backflow-prone areas.

#### 4. Relay Nodes
Used to bridge communications where direct uplink is unreliable.

#### 5. Beacon Nodes
Used to provide local visible status in areas where centralized monitoring may fail.

#### 6. Gateway Nodes
Used to aggregate multiple nearby nodes and forward state to higher-level systems.

---

## Functional Data Model

Each node should be capable of reporting some subset of the following:

- node identifier
- timestamp
- firmware version
- power state
- battery state
- enclosure health flag
- communication health
- water level
- water-level trend
- blockage score
- backflow flag
- debris score
- local alert state
- degraded-mode state
- maintenance-needed flag
- last service date
- local environmental notes

Not all node classes need all fields, but the architecture should aim for consistent naming and transport structure.

---

## State Model

Each node should operate using a clear and finite set of states.

### Suggested Core States

- **BOOT**
- **NORMAL**
- **WATCH**
- **ALERT**
- **DEGRADED**
- **FAULT**
- **MAINTENANCE**
- **OFFLINE_LOGGING**
- **SHUTDOWN_SAFE**

### Example State Interpretation

#### NORMAL
Conditions appear within expected operational bounds.

#### WATCH
A trend is deteriorating or a threshold is being approached.

#### ALERT
A meaningful flood, blockage, or dangerous water condition is active.

#### DEGRADED
The node remains partially useful, but one or more inputs or services are impaired.

#### FAULT
The node cannot presently be trusted for its intended role.

#### OFFLINE_LOGGING
The node cannot uplink but is still preserving local data.

#### SHUTDOWN_SAFE
The node has intentionally minimized activity to preserve itself or avoid unsafe behavior.

---

## Trust and Confidence Logic

Because flood decisions should not depend blindly on one sensor, IX-Bayanihan should prefer multi-factor interpretation.

### Confidence Inputs May Include

- recent successful sensor reads
- power stability
- communication quality
- self-test results
- enclosure health
- cross-checks between sensor channels
- trend consistency over time
- known maintenance status

### Confidence Outcomes

Signals can be flagged as:

- trusted
- cautionary
- degraded
- suspect
- unavailable

This reduces the risk of overreacting to bad reads or silent hardware drift.

---

## Interface Philosophy

The repository should support interfaces between modules using simple, inspectable contracts.

### Interface Priorities

- explicit naming
- stable field meanings
- timestamped records
- low-bandwidth tolerance
- degraded-mode compatibility
- log-first philosophy

### Desired Interface Types

- sensor-to-controller
- controller-to-local-alert
- node-to-gateway
- node-to-log-store
- node-to-operator-summary
- maintenance-record-to-node-history

The architecture should remain usable even if higher-level services are unavailable.

---

## Local Warning Philosophy

A field node should not depend exclusively on a distant dashboard.

Where useful, nodes may include:

- local LEDs
- local buzzers or sirens where context-appropriate
- maintenance indicators
- status blink codes
- local inspection labels

The purpose is not to create panic.
The purpose is to preserve local interpretability when centralized systems fail.

---

## Deployment Scales

The architecture supports multiple scales of deployment.

### Scale 1: Single Point Pilot
One or a few nodes at a known flood trouble spot.

### Scale 2: Street Segment Pilot
A set of nodes across several drains or one underpass corridor.

### Scale 3: Neighborhood Cluster
Street nodes, one or more channel nodes, and at least one gateway or relay node.

### Scale 4: District Flood Cell
Integrated flood monitoring over a broader municipal sub-area with maintenance and operator review.

### Scale 5: Metro-Integrated Layer
A larger-scale integration with public flood operations, pumps, gates, or broader city response tools.

The repository should be useful starting at Scale 1 and credible through Scale 4 proof-of-concept design.

---

## Fault Model

The architecture assumes faults will happen.

### Expected Fault Classes

- blocked sensor face
- sediment burial
- trash interference
- enclosure leak
- battery decline
- cable failure
- communications loss
- power surge
- false threshold trigger
- mounting failure
- mechanical jam in self-cleaning component
- software state freeze

### Fault Handling Philosophy

When faults occur, the node should do as many of these as possible:

- fail visibly
- log the event
- preserve service history
- enter degraded mode when appropriate
- prevent unsafe repetitive behavior
- simplify operator interpretation
- remain field-recoverable

---

## Proof-of-Concept Architecture Stack

The repository’s proof-of-concept pathway should be built around three practical modules.

### PoC Module 1: Smart Inlet Node
A small field-buildable unit for monitoring water rise and inferred blockage at a street drain or inlet.

### PoC Module 2: Outfall or Channel Sentinel Node
A more exposed monitoring unit for water level, backflow, and condition visibility at an estero, canal edge, or outfall.

### PoC Module 3: Flood Operations Console
A lightweight local software layer or dashboard that receives events, scores severity, and displays node states and faults.

These three together form a coherent demonstration of the project’s intended value.

---

## System Boundary

IX-Bayanihan stops at the point where a builder would need:

- large civil works engineering
- stamped construction drawings
- large municipal pump design authority
- floodwall or surge-gate structural design authority
- basin-scale hydraulic approval
- emergency management command authority

The repository may support those systems with better information, but it does not replace them.

---

## Architecture Summary Statement

IX-Bayanihan is best understood as:

> **A layered, modular flood-resilience architecture for sensing, blockage awareness, local warning, telemetry continuity, and operator decision support in flood-prone environments.**

Its strength does not come from one dramatic device.

Its strength comes from combining:

- small local awareness
- corridor-level observation
- resilient power and logging
- disciplined degraded-mode behavior
- clear maintenance pathways
- open, reusable field logic

That is the core architecture this repository will build around.
