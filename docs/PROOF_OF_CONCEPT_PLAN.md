# IX-Bayanihan Proof of Concept Plan

## Purpose

This document defines the initial proof-of-concept pathway for **IX-Bayanihan**.

The purpose of the proof of concept is not to pretend that a small prototype resolves citywide flooding.

The purpose is to demonstrate that a modular, open, field-buildable flood-support system can do useful work in real conditions by improving:

- rising-water awareness
- blockage detection
- drain failure visibility
- local warning capability
- telemetry continuity
- degraded-mode behavior
- event logging
- maintenance prioritization

This document defines what the first proof of concept should include, what it should prove, what it should not claim, and how it should be tested.

---

## Proof-of-Concept Objective

The proof of concept should answer this question:

> Can a small, modular IX-Bayanihan deployment detect flood-relevant conditions early enough and clearly enough to improve local visibility and response at real flood trouble points?

This is the correct early question.

The proof of concept is not a final deployment package.
It is an evidence-building step.

---

## Proof-of-Concept Philosophy

The proof of concept should be:

- small enough to build
- serious enough to test outdoors
- simple enough to troubleshoot
- instrumented enough to learn from
- honest enough to avoid inflated claims

A weak proof of concept only shows that parts turn on.

A strong proof of concept shows that the system behaves in a disciplined way when conditions deteriorate.

---

## What the Proof of Concept Must Demonstrate

The initial IX-Bayanihan proof of concept should demonstrate all of the following:

### 1. Water Rise Detection
The system can detect meaningful water-level changes at selected flood-prone points.

### 2. Condition Classification
The system can distinguish at least some difference between:

- normal condition
- watch condition
- alert condition
- degraded or faulty condition

### 3. Local Visibility
The system provides visible local status even if centralized monitoring is unavailable.

### 4. Event Logging
The system records threshold crossings, faults, and state changes in a usable way.

### 5. Basic Fault Tolerance
The system behaves predictably when communications are lost, power dips, or a sensor becomes unreliable.

### 6. Practical Maintenance Signals
The system can mark when a node likely needs cleaning, inspection, or service.

### 7. Real Outdoor Behavior
The system survives short-duration deployment in real outdoor flood-prone conditions long enough to produce useful evidence.

---

## What the Proof of Concept Must Not Claim

The initial proof of concept must **not** claim to do any of the following:

- prevent typhoons
- stop monsoon rain
- eliminate flooding
- replace public works
- replace engineered drainage projects
- replace pumps or gates
- predict every flood accurately
- guarantee life safety
- guarantee property protection
- prove district-wide effectiveness from one small test

A proof of concept that makes those claims would be dishonest.

---

## Recommended Proof-of-Concept Scope

The first IX-Bayanihan proof of concept should include **three modules**.

### PoC Module A — Smart Inlet Node
A compact node placed at or near a drain, curb inlet, sump edge, or low roadside collection point.

Purpose:
- detect rising water
- infer possible blockage or poor drainage behavior
- provide local alert state
- log conditions and faults

### PoC Module B — Channel or Outfall Sentinel Node
A more exposed node placed at a drainage channel edge, estero, culvert mouth, outfall edge, or similar water corridor.

Purpose:
- monitor broader water behavior
- watch for elevated downstream condition
- support backflow or overflow awareness
- maintain telemetry continuity from a strategic point

### PoC Module C — Local Flood Operations Console
A lightweight operator-facing software or dashboard layer.

Purpose:
- display node states
- show alert transitions
- show last-seen health
- show maintenance flags
- preserve event history
- provide a simple local summary of conditions

These three modules together form a coherent minimum proof of concept.

---

## Why These Three Modules Are the Right Starting Point

This three-part structure gives the project enough breadth to be taken seriously.

It shows:

- a street-level view
- a corridor-level view
- an operator-level view

That matters because local flooding is often misunderstood when only one perspective exists.

One drain alone is too small a story.
A dashboard with no hardware is empty.
A channel node without street context is incomplete.

This three-module structure is the minimum configuration that demonstrates system thinking.

---

## Proof-of-Concept Deployment Model

The first proof of concept should be built in stages.

### Stage 1 — Bench Validation
Validate sensors, local states, event logs, alert logic, and fault handling indoors or under controlled conditions.

### Stage 2 — Controlled Water Testing
Use safe, repeatable water-level tests to simulate rising water, persistent ponding, and recovery.

### Stage 3 — Short Outdoor Dry Run
Deploy hardware outdoors without waiting for a flood event to test enclosure, power, communications, and service access.

### Stage 4 — Opportunistic Storm Observation
Observe real-world weather events or known runoff conditions in a safe and non-invasive deployment.

### Stage 5 — Post-Test Review
Examine logs, false positives, false negatives, service issues, sensor drift, and visibility quality.

This staged path is important because too many projects jump from theory to chaos and then learn nothing useful.

---

## Proof-of-Concept Node Targets

The proof of concept should focus on locations that are likely to teach something meaningful.

### Good Candidate Locations

- curb inlets that frequently pond during storms
- roadside drains that collect visible debris
- low alleys or small depressions
- underpass edges where standing water begins
- known drainage channels with visible rise behavior
- outfall-adjacent points with backflow suspicion
- culvert edges where overflow or blockage is plausible

### Poor Candidate Locations

- places with no known flood relevance
- places where access is unsafe
- places where mounting is not secure
- places where vandalism or theft is highly likely
- places where installation would violate local rules
- places where service crews cannot reach the hardware

The first proof of concept should favor learnable sites over dramatic ones.

---

## Minimum Technical Capabilities for Each PoC Module

## Module A — Smart Inlet Node Minimum Capabilities

The initial smart inlet node should include:

- water-level sensing
- a local threshold state machine
- local visible indicator
- event logging
- enclosure health awareness where possible
- power-state awareness
- simple maintenance-needed flag logic

It should be able to transition through at least:

- NORMAL
- WATCH
- ALERT
- DEGRADED
- FAULT

### Minimum Smart Inlet PoC Questions

- Does the node detect meaningful rise fast enough?
- Does it recover properly as water drops?
- Can it indicate likely blockage or persistent ponding?
- Does the alert logic remain understandable?
- Can the node stay useful if communications fail?

---

## Module B — Channel or Outfall Sentinel Minimum Capabilities

The initial channel or outfall node should include:

- water-level sensing
- trend tracking over time
- local health indicator
- event logging
- power-state reporting
- communications heartbeat
- exposed-environment mounting logic

Where feasible, it may also include:

- enclosure humidity sensing
- backflow inference logic
- optional camera-assisted observation
- optional local beacon

### Minimum Sentinel PoC Questions

- Does the node provide meaningful broader context beyond the street node?
- Can it survive a dirtier, wetter, more exposed deployment?
- Does it preserve logs during intermittent connectivity?
- Does its condition help explain why street drainage may be failing?

---

## Module C — Local Flood Operations Console Minimum Capabilities

The first operations console should be simple, not bloated.

It should show:

- node list
- last seen timestamp
- node state
- water-level or trend status
- fault state
- maintenance-needed flag
- local event history
- basic severity summary

The operations console should **not** try to impersonate a full emergency-management platform.

### Minimum Operations Console PoC Questions

- Can a user understand what is happening quickly?
- Can the console distinguish node faults from flood alerts?
- Does the event history remain usable after a disruption?
- Can the console show enough information to guide inspection or cleanup?

---

## PoC Functional Success Criteria

The proof of concept should be considered functionally successful if it demonstrates all of the following.

### Success Criterion 1 — Repeatable Threshold Behavior
The nodes enter and exit state transitions in a repeatable and understandable way.

### Success Criterion 2 — Usable Logs
The event history is clear enough to reconstruct what happened.

### Success Criterion 3 — Local Interpretability
A field observer can understand a node’s local state without needing a full software stack.

### Success Criterion 4 — Basic Fault Separation
The system distinguishes between "real water problem" and "hardware problem" often enough to remain useful.

### Success Criterion 5 — Outdoor Survivability
The node survives short pilot exposure without immediate enclosure or power collapse.

### Success Criterion 6 — Maintenance Value
The proof of concept reveals something actionable about cleaning, servicing, or placement.

### Success Criterion 7 — Learning Value
The results teach the builder where the design is weak, not just where it looks good.

---

## PoC Failure Criteria

The proof of concept should be considered weak or failed if any of the following dominate:

- thresholds behave randomly
- sensor data is unstable and unexplained
- logs are too poor to interpret
- nodes fail quickly outdoors
- local status is confusing
- maintenance access is terrible
- mounting is unreliable
- communications loss destroys useful evidence
- the deployment learns nothing practical
- claims exceed what the data supports

A flashy demo that teaches nothing is not a success.

---

## Test Conditions the PoC Should Cover

The proof of concept should include tests that cover at least the following conditions.

### 1. Normal Dry Condition
The node runs in a stable baseline state.

### 2. Rising Water Condition
Water level rises through one or more thresholds.

### 3. Persistent Water Condition
Water remains above expected recovery level for a meaningful duration.

### 4. Recovery Condition
Water level drops back toward normal and the node responds properly.

### 5. Communications Loss
The node enters offline logging or another degraded communication behavior.

### 6. Power Dip or Power Change
The node demonstrates safe behavior when power is unstable or switched.

### 7. Sensor Error or Invalid Read
The node handles suspicious data without pretending everything is fine.

### 8. Maintenance Reset or Service Event
The node supports a controlled maintenance state or logged service action.

These conditions are more useful than one dramatic flood clip.

---

## Suggested PoC Metrics

The proof of concept should collect metrics that matter.

### Detection Metrics
- time from water rise to WATCH
- time from water rise to ALERT
- persistence duration
- recovery time to NORMAL

### Reliability Metrics
- uptime during deployment
- communications uptime
- successful log write rate
- number of unexplained resets
- number of sensor read failures

### Maintenance Metrics
- number of service visits needed
- time required to open and inspect the unit
- visible debris load condition
- signs of sediment or water ingress
- battery condition after deployment

### Usefulness Metrics
- whether the node captured meaningful event transitions
- whether the operator display remained understandable
- whether the deployment changed what would be inspected or cleaned first

---

## Recommended PoC Test Sequence

The first proof of concept should follow a disciplined sequence.

### Phase 1 — Bench Bring-Up
- verify controller boot
- verify sensor read
- verify threshold transitions
- verify local alerts
- verify log file creation
- verify fault-state entry

### Phase 2 — Controlled Wet Test
- simulate rising water
- hold at watch threshold
- hold at alert threshold
- simulate recovery
- simulate persistent ponding
- simulate invalid sensor read

### Phase 3 — Outdoor Stability Test
- deploy hardware outside in noncritical conditions
- observe enclosure heat, humidity, and power behavior
- verify communications range
- inspect physical mounting

### Phase 4 — Real Weather Observation
- operate during real rain or runoff events where safe
- compare node behavior to visible site conditions
- compare street and channel node correlation

### Phase 5 — Post-Event Analysis
- read logs
- inspect missed detections
- inspect false triggers
- inspect degraded-mode entries
- record service and physical wear findings

---

## Required Outputs of the Proof of Concept

A serious proof of concept should produce more than a hardware photo.

It should produce:

- assembly evidence
- wiring evidence
- mounting evidence
- event logs
- test notes
- maintenance notes
- fault notes
- state transition records
- lessons learned
- a clear next-step recommendation

These outputs make the project believable.

---

## PoC Safety Boundaries

The proof of concept must follow strict safety discipline.

### It should never require:
- entering dangerous floodwater
- unsafe road exposure
- attachment to critical public infrastructure without permission
- energized work without proper controls
- enclosed-space entry
- unsafe ladder or channel-edge work
- storm chasing behavior
- improvised mains wiring

Proof of concept does not justify reckless field work.

---

## Recommended Documentation Produced by the PoC

Each proof-of-concept deployment should document:

### Before Deployment
- site description
- node purpose
- deployment date
- hardware revision
- firmware revision
- expected thresholds
- mounting method
- power method

### During Deployment
- notable weather or runoff conditions
- visible water behavior
- debris observations
- communications observations
- service interventions
- unexpected behavior

### After Deployment
- retrieved logs
- enclosure inspection findings
- battery status
- sensor condition
- water ingress findings
- maintenance notes
- threshold tuning notes
- next design revision list

---

## PoC Revision Doctrine

The proof of concept should not be treated as a final object.

Its purpose is to reveal what to improve.

After the first proof of concept, revisions should focus on the real weak points such as:

- sensor placement
- ingress protection
- battery endurance
- communications resilience
- mounting geometry
- clog inference quality
- alert visibility
- maintenance burden
- false-trigger handling

A good proof of concept creates a disciplined revision path.

---

## Recommended PoC Deliverables for This Repository

The IX-Bayanihan repository should eventually include these proof-of-concept deliverables:

1. A node-specific proof-of-concept BOM
2. A proof-of-concept wiring diagram
3. A proof-of-concept assembly walkthrough
4. A field deployment checklist
5. A basic test checklist
6. A sample event log schema
7. A simple operations console mock or implementation
8. A known-limitations note
9. A revision feedback template

These should be sufficient for another builder to reproduce the work.

---

## PoC Summary Statement

The IX-Bayanihan proof of concept is meant to prove something useful and bounded:

> A small, open, modular flood-support system can detect meaningful conditions, remain interpretable during degraded conditions, and provide actionable visibility at local flood trouble points.

That is enough to justify further work.

It is also honest.

The proof of concept exists to build evidence, not mythology.
