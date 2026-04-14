# IX-Bayanihan

**IX-Bayanihan** is an open humanitarian flood-resilience repository for modular flood-support hardware, software, and field procedures.

It is built to help communities, builders, NGOs, researchers, and public-interest implementers improve flood awareness and response through practical, field-buildable systems that support:

- rising-water detection
- drain and inlet failure awareness
- debris and blockage visibility
- outfall and channel condition awareness
- local warning and telemetry continuity
- maintenance prioritization
- event logging
- operator-facing flood visibility

This project is **Philippines-first in design intent** and structured for reuse anywhere flood-prone communities need open, practical tools.

---

## License

This repository is released under the **GNU Affero General Public License v3.0**.

That means the code and repository contents are intended to stay open and shareable. Anyone can study, use, modify, and redistribute the project under the terms of AGPL-3.0.

See the root `LICENSE` file for the full license text.

---

## What IX-Bayanihan Is

IX-Bayanihan is a **layered flood-resilience architecture**.

It is not one miracle machine.

It is a structured stack of compatible components meant to help communities see and respond to flood-relevant conditions earlier and more clearly.

At its core, IX-Bayanihan is built around three practical proof-of-concept modules:

1. **Smart Inlet Node**  
   A local street-facing node for drains, curb inlets, sumps, and low collection points.

2. **Channel / Outfall Sentinel Node**  
   A corridor-facing node for esteros, channels, culverts, outfalls, and backflow-prone drainage points.

3. **Local Flood Operations Console**  
   A lightweight operator-facing layer that makes node states, events, faults, and maintenance flags understandable.

These modules are supported by:

- tiered BOMs
- assembly walkthroughs
- schema definitions
- proof-of-concept planning
- test checklists
- deployment checklists
- inspection and maintenance guidance

---

## What IX-Bayanihan Is Not

IX-Bayanihan does **not** claim to:

- stop typhoons
- stop monsoons
- stop rainfall at cloud level
- eliminate all flooding
- replace major drainage works
- replace public flood-control infrastructure
- replace pumps, gates, barriers, or basin-scale engineering
- replace evacuation planning
- replace licensed engineering review
- guarantee life safety
- guarantee property protection

This repository should be framed honestly.

The purpose of IX-Bayanihan is to improve **visibility, detection, resilience, and local operational understanding** around real flood pain points.

It is not a flood cure.

---

## Why This Project Exists

Many flood failures become more dangerous because people learn too late that:

- a drain is blocked
- an inlet is not clearing
- a channel is already too high
- an outfall is backing up
- a node is dead or lying
- a site needs maintenance before the next storm
- field conditions are deteriorating faster than expected

IX-Bayanihan exists to reduce preventable flood harm by improving local visibility and coordination with open, buildable, field-oriented tools.

---

## Project Goals

The project is designed to help with these practical problems:

### 1. Street-Level Flood Awareness
Detect rising water near drains, inlets, sumps, alleys, low intersections, and underpasses.

### 2. Drainage Failure Detection
Identify when local drainage behavior suggests blockage, overload, persistent ponding, or poor discharge.

### 3. Channel and Outfall Visibility
Observe broader corridor conditions that can explain why local drainage is failing.

### 4. Telemetry Continuity
Keep useful information alive when communications degrade or power becomes unstable.

### 5. Maintenance Prioritization
Surface which sites likely need cleaning, inspection, repair, or follow-up first.

### 6. Better Incident Review
Preserve logs and state changes so builders and operators can reconstruct what happened after an event.

---

## Core Proof-of-Concept Stack

The first serious IX-Bayanihan demonstration is built around three modules.

### Smart Inlet Node

The Smart Inlet Node is the street-facing module.

It is intended for:

- curb inlets
- roadside drains
- alley drains
- low roadside collection points
- small sumps
- underpass approach drains

Its job is to help answer:

- Is water rising near the drain?
- Is the condition persistent instead of clearing?
- Is this site likely blocked or overloaded?
- Does this location need inspection or cleaning?

### Channel / Outfall Sentinel Node

The Sentinel Node is the corridor-facing module.

It is intended for:

- esteros
- channels
- canals
- culvert mouths
- outfalls
- backflow-prone discharge points
- river-adjacent drainage corridors

Its job is to help answer:

- Is the broader corridor already high?
- Is downstream condition preventing local drainage from clearing well?
- Is backflow likely?
- Is this broader corridor helping explain neighborhood flooding?

### Local Flood Operations Console

The console is the interpretation layer.

It is intended to show:

- current node states
- last-seen health
- recent event history
- maintenance-needed status
- fault separation
- node detail
- simple severity framing

Its job is to make the field nodes understandable without pretending to be a full emergency-management platform.

---

## System Architecture

IX-Bayanihan is organized as a layered system.

### Layer A — Street and Inlet Layer
Local nodes placed at drains, curb inlets, sumps, and low points.

### Layer B — Channel and Outfall Layer
Monitoring nodes placed at esteros, channels, outfalls, culverts, and backflow-prone points.

### Layer C — Power and Communications Continuity Layer
Low-voltage power, logging, and communications discipline that keeps nodes useful during unstable conditions.

### Layer D — Flood Operations and Decision Layer
Thresholding, event logging, degraded-mode handling, fault visibility, and operator-facing interpretation.

### Layer E — Field Deployment and Maintenance Layer
Mounting, inspection, service access, maintenance intervals, and post-event review.

The strength of the project comes from these layers working together.

---

## BOM Tiers

IX-Bayanihan uses a tiered BOM system so builders can start honestly and scale deliberately.

### Tier 1 — Bench and Classroom Proof of Concept
For indoor validation, firmware bring-up, basic sensing tests, and early logic checks.

### Tier 2 — Field Pilot Node
For short outdoor deployments in real flood-prone conditions with practical hardening.

### Tier 3 — Hardened Community Node
For repeated outdoor use with stronger enclosure, protection, serviceability, and environmental resilience.

### Tier 4 — District Integration Reference
For multi-node deployments, gateways, operations visibility, and broader system coordination.

This tier model exists to prevent two common failures:

- overclaiming a weak build
- overbuilding before the basics are proven

---

## Proof-of-Concept Build Path

The recommended path through the repository is:

1. build the Smart Inlet Node proof of concept
2. build the Channel / Outfall Sentinel Node proof of concept
3. use the Local Flood Operations Console to view their states and events
4. test on the bench
5. run controlled wet tests
6. perform an outdoor dry run
7. perform safe real-condition observation
8. inspect, maintain, revise, and repeat

This repository is designed around disciplined progression, not hype.

---

## Repository Layout

```text
IX-Bayanihan/
├── LICENSE
├── README.md
├── docs/
├── bom/
├── hardware/
├── firmware/
├── software/
├── schemas/
├── sim/
├── field/
├── tests/
├── assets/
└── licenses/

Directory Summary
docs/

Architecture, project scope, claim boundaries, BOM tiers, proof-of-concept planning, and system definitions.

bom/

Node-specific bill-of-materials files tied to real builds and deployment tiers.

hardware/

Assembly walkthroughs, enclosure notes, mounting logic, and physical build guidance.

firmware/

Embedded logic for field nodes, including state handling, thresholding, logging, and degraded-mode behavior.

software/

Operator-facing console and supporting tools.

schemas/

Structured definitions for node status and event records.

sim/

Future scenario and replay inputs for testing logic without waiting for storms.

field/

Deployment, inspection, and maintenance guidance.

tests/

Bench tests, wet-test checklists, and proof-of-concept validation material.

assets/

Supporting visual materials and diagrams.

licenses/

Supplementary notice files if needed later.

Current Repository Spine

The current repository is built around these foundational files.

Project and Architecture
docs/PROJECT_SCOPE_AND_CLAIM_BOUNDARY.md
docs/SYSTEM_ARCHITECTURE.md
docs/BOM_TIERS.md
docs/PROOF_OF_CONCEPT_PLAN.md
docs/POC_MODULE_SPECIFICATIONS.md
docs/REPOSITORY_LAYOUT.md
Proof-of-Concept BOMs
bom/poc/smart_inlet_node_bom.md
bom/poc/sentinel_node_bom.md
Assembly Walkthroughs
hardware/smart_inlet_node/assembly_walkthrough.md
hardware/sentinel_node/assembly_walkthrough.md
Console Specification
software/ops_console/console_spec.md
Schemas
schemas/node_status/node_status.schema.json
schemas/event_logs/event_log.schema.json
Testing and Field Use
tests/bench/poc_test_checklist.md
field/checklists/deployment_checklist.md
field/maintenance/inspection_and_maintenance_checklist.md

These files are the project backbone.

What Builders Can Actually Do With This Repository

IX-Bayanihan is useful when it helps a builder do concrete work.

A builder should be able to use this repository to:

understand the project boundary clearly
choose an appropriate deployment tier
source parts for a proof-of-concept Smart Inlet Node
source parts for a proof-of-concept Sentinel Node
assemble those nodes with a disciplined process
validate node behavior using structured checklists
deploy pilot hardware safely and with records
maintain and inspect field hardware honestly
build a lightweight operations view around node status and event logs

That is real value.

What Makes This Credible

This repository is designed to be believable because it focuses on:

bounded claims
modular architecture
real assembly pathways
tiered BOM logic
logging and evidence preservation
degraded-mode behavior
maintenance discipline
deployment discipline
honest limitations

The project is strongest when it remains boring in the best engineering sense:

clear
reproducible
testable
serviceable
useful
How This Helps Flood-Prone Communities

IX-Bayanihan is meant to help at the level where many flood failures first become dangerous.

It can help communities and implementers:

detect worsening local drainage conditions earlier
see where repeat blockage or ponding occurs
understand whether a corridor or outfall condition is contributing to local flooding
keep useful local data even when communications are weak
decide what needs inspection or maintenance sooner
review real event timelines after storms

This is meaningful help, even though it is not the same thing as solving citywide flooding by itself.

Build and Use Doctrine

IX-Bayanihan should be used with the following discipline.

Do
build small first
test before claiming
log everything that matters
treat degraded mode as normal engineering reality
maintain field hardware regularly
document deviations from the BOM and assembly guides
reject bad deployments instead of forcing them
Do Not
overclaim what the proof of concept proves
treat one successful node as a citywide answer
ignore maintenance
hide faults behind vague language
treat communications failure as the same thing as a flood condition
deploy unsafe hardware in dangerous conditions
use the project to imply guaranteed protection
Suggested First Read Order

For a new serious reader, the strongest order is:

docs/PROJECT_SCOPE_AND_CLAIM_BOUNDARY.md
docs/SYSTEM_ARCHITECTURE.md
docs/BOM_TIERS.md
docs/PROOF_OF_CONCEPT_PLAN.md
docs/POC_MODULE_SPECIFICATIONS.md
bom/poc/smart_inlet_node_bom.md
bom/poc/sentinel_node_bom.md
hardware/smart_inlet_node/assembly_walkthrough.md
hardware/sentinel_node/assembly_walkthrough.md
tests/bench/poc_test_checklist.md
field/checklists/deployment_checklist.md
field/maintenance/inspection_and_maintenance_checklist.md

That path takes the reader from concept to build to deployment discipline.

Intended Users

IX-Bayanihan is meant to be useful to:

community builders
disaster resilience volunteers
NGOs
researchers
prototype teams
technically capable local implementers
public-interest engineers
flood-prone communities looking for open modular approaches

It is written so the project can stand on its own without private context.

Safety and Responsibility

Nothing in this repository should be interpreted as permission to:

enter dangerous floodwater
access unauthorized infrastructure
perform unsafe electrical work
ignore local law, local authority, or local engineering requirements
substitute prototype hardware for formal public safety systems

Builders are responsible for safe deployment, lawful access, and disciplined interpretation of results.

Long-Term Direction

The strongest long-term direction for IX-Bayanihan is:

improved field node hardening
refined schemas and event models
stronger proof-of-concept firmware
simple but credible operations software
clearer field deployment templates
better maintenance history support
multi-node district pilot pathways
stronger documentation for community reuse

The project should grow by making the build path stronger, not by inflating claims.

Project Standard Statement

IX-Bayanihan is an open humanitarian flood-resilience repository for modular sensing, blockage awareness, local warning, telemetry continuity, maintenance visibility, and operator-facing flood support.

It is built to help communities understand and respond to real flood pain points more clearly.

It is not built to make impossible claims.

That boundary is intentional.

Author and Attribution

Project authorship and attribution for repository work may use:

Bryce Lovell

If future public documentation includes attribution or maintainership notes, keep the project framing consistent with the purpose of this repository.

Final Note

The most important thing about IX-Bayanihan is not that it sounds ambitious.

It is that it remains useful, open, honest, and buildable.

That is what gives the project real value.
