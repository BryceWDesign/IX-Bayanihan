# IX-Bayanihan Project Scope and Claim Boundary

## Purpose

**IX-Bayanihan** is an open humanitarian flood-resilience project focused on helping communities detect, understand, and respond to dangerous flooding with practical, buildable, modular tools.

The project is designed to support:

- early flood detection
- drain and inlet failure detection
- debris and blockage awareness
- water-level monitoring
- local warning and telemetry continuity
- pump and gate coordination support
- operator decision support
- field deployment in flood-prone urban environments

The project is **Philippines-first in design intent**, but it is structured so the same methods can be adapted for other flood-prone regions.

---

## What IX-Bayanihan Is

IX-Bayanihan is a **flood-resilience architecture**.

It is not one single machine.  
It is a structured stack of compatible parts, including:

- low-power field sensing nodes
- smart drain and inlet monitoring units
- estero, canal, river, and outfall monitoring nodes
- debris and blockage detection logic
- local alerting hardware
- telemetry and event logging
- operator-facing flood decision support
- proof-of-concept control logic for safer flood operations

The project is meant to help communities and builders create systems that improve visibility, coordination, and resilience during flood events.

---

## Primary Design Objective

The primary design objective of IX-Bayanihan is:

> **Reduce preventable flood harm by improving local flood awareness, infrastructure visibility, drainage fault detection, and response coordination using open, buildable, field-oriented designs.**

This project is built around the idea that many flood failures become catastrophic because warning, monitoring, blockage awareness, and infrastructure visibility arrive too late.

---

## Core Humanitarian Framing

IX-Bayanihan is intended to be:

- open
- practical
- modular
- field-serviceable
- low-cost where possible
- honest about limitations
- usable by communities, builders, responders, researchers, NGOs, and public-interest implementers

The project exists to increase the number of people who can build useful flood-support systems without waiting for a closed or proprietary vendor ecosystem.

---

## Non-Goals

IX-Bayanihan does **not** claim to do the following:

- stop typhoons
- stop monsoons
- stop rainfall at cloud level
- eliminate all flooding
- replace river-basin engineering
- replace major pump stations
- replace drainage master plans
- replace coastal barriers
- replace storm-surge infrastructure
- replace evacuation planning
- replace professional engineering review
- replace local codes, standards, or regulatory approvals

This project does **not** claim to solve national or citywide flooding by itself.

Any statement implying that IX-Bayanihan can make floodwater disappear, prevent storms from forming, or fully resolve compound flood risk would be false and is outside the boundaries of this repository.

---

## What IX-Bayanihan Can Reasonably Help With

IX-Bayanihan is intended to help with the following practical pain points:

### 1. Street-Level Flood Awareness
Detect rising water in vulnerable streets, alleys, underpasses, curb inlets, sumps, and low points before conditions worsen.

### 2. Drainage Failure Detection
Identify when drains, inlets, culverts, or intake screens are blocked, overloaded, backflowing, or failing to evacuate water.

### 3. Debris and Trash Choke Awareness
Improve visibility into the trash and debris conditions that commonly reduce flood-control effectiveness.

### 4. Telemetry Continuity During Storms
Keep critical monitoring alive during poor weather, unstable power conditions, or partial infrastructure failure.

### 5. Better Maintenance Prioritization
Show where crews should clean, inspect, repair, or clear blockages first.

### 6. Better Operational Decision Support
Support safer decisions for gates, pumps, warnings, and field deployment by improving visibility and evidence.

### 7. Faster Local Response
Improve the speed at which communities and operators recognize deteriorating conditions and act on them.

---

## Design Doctrine

IX-Bayanihan follows seven design rules.

### Rule 1: Solve Real Flood Problems, Not Cinematic Ones
The project focuses on water movement, drainage failure, backflow, debris, telemetry, and operations. It does not chase speculative weather-control concepts.

### Rule 2: Visibility Before Complexity
A simple, well-instrumented flood node is more valuable than a dramatic concept that cannot be verified or maintained.

### Rule 3: Local Failure Matters
A blocked drain, jammed intake, dead battery, flooded pump room, or silent sensor can turn a manageable event into a dangerous one. Small failures matter.

### Rule 4: Degraded Mode Is Normal
Flood systems must keep working in partial failure states. Communication loss, low power, sensor drift, and mechanical degradation must be expected.

### Rule 5: Serviceability Is a Requirement
Anything built under this project should be understandable, repairable, and replaceable in the field.

### Rule 6: Claims Must Stay Inside Evidence
No module in this repository should promise more than it can demonstrate.

### Rule 7: Open Systems Must Still Be Disciplined
Open access does not justify vague engineering. Designs must remain structured, labeled, and testable.

---

## Intended Deployment Environments

The project is designed with these environments in mind:

- dense urban neighborhoods
- flood-prone streets and intersections
- curb inlets and roadside drains
- underpasses
- pump station approaches
- esteros and drainage channels
- outfalls
- river-adjacent settlements
- low-lying coastal or backflow-prone areas
- community-scale pilot sites
- municipal demonstration districts

---

## Functional Layers of the Repository

The repository will be organized around a practical flood-support stack.

### Layer A: Smart Inlet and Street Drain Layer
For local detection of rising water, blocked drainage, intake clogging, and street-level flood deterioration.

### Layer B: Channel, Estero, and Outfall Layer
For water-level awareness, backflow detection, debris observation, and remote alerting in exposed drainage corridors.

### Layer C: Power and Communications Continuity Layer
For keeping field nodes alive long enough to remain useful during storms and outages.

### Layer D: Flood Operations and Decision Layer
For event logging, thresholding, degraded-mode behavior, field alerting, and future pump/gate coordination support.

### Layer E: Deployment and Maintenance Layer
For installation logic, inspection practice, fault handling, maintenance intervals, and field replacement procedures.

---

## Proof-of-Concept Boundary

Any proof of concept in IX-Bayanihan should be understood as one of the following:

- a field node proof of concept
- a monitoring proof of concept
- a telemetry proof of concept
- a blockage-detection proof of concept
- a power-continuity proof of concept
- a decision-support proof of concept

A proof of concept in this repository is **not** equivalent to a validated citywide flood-control deployment.

A proof of concept only demonstrates that a module or workflow is plausible enough to test under controlled or limited field conditions.

---

## Safety Boundary

IX-Bayanihan is not a life-critical certified safety system.

No file in this repository should be interpreted as:

- a stamped engineering package
- a final construction drawing set
- a replacement for licensed review
- a guarantee of flood survival
- a guarantee of property protection
- a substitute for evacuation orders
- a substitute for official warnings

Users must assume that any deployment requires local engineering judgment, environmental review, field validation, and safety oversight.

---

## Public Communication Boundary

When this project is described publicly, it should be described using language like:

- open humanitarian flood-resilience architecture
- modular flood monitoring and response support system
- smart drainage and flood-operations support stack
- open field-buildable tools for flood awareness and infrastructure visibility
- Philippines-first open flood-support project with global reuse potential

It should **not** be described as:

- a flood cure
- a typhoon stopper
- a weather-control system
- a guaranteed flood prevention machine
- a complete replacement for public works
- a complete solution to Manila flooding by itself

---

## Success Criteria

IX-Bayanihan should be judged by whether it can demonstrate useful progress in areas like:

- faster flood condition awareness
- earlier blockage detection
- stronger local telemetry continuity
- better maintenance targeting
- improved incident logging
- clearer field deployment logic
- safer degraded-mode behavior
- credible proof-of-concept assembly and testing
- practical reuse by other communities

---

## Failure Criteria

The project should be considered off-track if it drifts into any of the following:

- exaggerated claims
- untestable hardware narratives
- unclear or unverifiable BOMs
- vague diagrams without assembly path
- systems that cannot survive field conditions
- modules that require unrealistic conditions to work
- hidden dependencies
- flood claims with no observable test method
- writing that implies miracle-scale performance

---

## Scope Discipline for Contributors

Future additions to IX-Bayanihan should satisfy this test:

> **Does this module help a real flood-prone community detect, understand, coordinate around, or physically manage flooding in a practical way?**

If the answer is no, the module should not be included.

If the answer is only "maybe, if stretched," the module should be treated with caution and kept out unless it can be made concrete.

---

## Repository Standard Statement

IX-Bayanihan is an open humanitarian engineering repository for modular flood-resilience tools.

It is built to improve:

- visibility
- coordination
- detection
- resilience
- field serviceability
- public usefulness

It is not built to make impossible claims.

That boundary is intentional and must remain intact across the entire repository.
