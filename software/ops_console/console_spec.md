# IX-Bayanihan Local Flood Operations Console Specification

## Purpose

This document defines the initial specification for the **IX-Bayanihan Local Flood Operations Console**.

The console is the operator-facing part of the proof-of-concept system.

Its job is not to control a city.
Its job is to make the field nodes understandable.

The console exists to turn raw node behavior into usable local flood awareness by showing:

- what is happening
- where it is happening
- which nodes are healthy
- which nodes are degraded
- which sites likely need inspection
- what changed recently
- what evidence was captured

This is a **lightweight operational visibility layer**, not a full emergency-management platform.

---

## Scope Boundary

The Local Flood Operations Console is designed for:

- proof-of-concept demonstrations
- pilot deployments
- community-scale monitoring
- NGO or public-interest evaluation
- local maintenance prioritization
- post-event review
- simple multi-node situational awareness

It is **not** designed to be:

- an official government flood warning system
- a life-safety-certified command platform
- a basin-scale hydrologic model
- a replacement for professional emergency operations centers
- an autonomous controller for major pumps or floodgates

The console should stay honest and clear about this boundary.

---

## Primary Mission

The console exists to answer these questions quickly:

- Which nodes are normal?
- Which nodes are approaching concern?
- Which nodes are already in alert?
- Which nodes are degraded or faulty?
- Which nodes have gone silent?
- What changed in the last few minutes or hours?
- Which locations should be inspected first?
- Do the street and channel nodes tell a coherent story?

If the console cannot answer those questions clearly, it is failing its purpose.

---

## Console Design Philosophy

The console should follow six rules.

### Rule 1: Clarity Over Flash
The first version should favor readability and operational clarity over visual drama.

### Rule 2: Faults Must Not Look Like Floods
Hardware problems and flood conditions must be visually separated.

### Rule 3: The Node State Is the Core Unit
The interface should be built around clear per-node state and recent changes.

### Rule 4: Logs Matter
Recent event history must remain accessible because flood understanding is temporal, not just static.

### Rule 5: Low Complexity Wins Early
A smaller, cleaner console is more believable than a bloated fake command center.

### Rule 6: Offline Grace Matters
The console should remain useful even when data is late, partial, or temporarily stale.

---

## Console Role in the Proof of Concept

The proof-of-concept system includes three modules:

1. Smart Inlet Node
2. Channel / Outfall Sentinel Node
3. Local Flood Operations Console

The console is the part that ties the node outputs into a coherent operator view.

The console does not create the evidence.
It organizes the evidence.

That distinction matters.

---

## Minimum Functional Requirements

The Local Flood Operations Console should support the following minimum capabilities.

### 1. Node Summary View
Display every known node with its current state, last-seen timestamp, and basic health.

### 2. State Visibility
Display explicit states such as:

- NORMAL
- WATCH
- ALERT
- DEGRADED
- FAULT
- OFFLINE_LOGGING

### 3. Last-Seen Visibility
Show whether a node is:
- actively reporting
- delayed
- stale
- logging locally but not uplinking
- possibly offline

### 4. Recent Event History
Show recent state transitions, faults, and maintenance-relevant changes.

### 5. Maintenance Flag Visibility
Show which nodes appear to need cleaning, inspection, or service.

### 6. Basic Severity Framing
Provide an understandable way to identify the most concerning nodes without hiding the raw node state.

### 7. Simple Site Detail View
Allow the user to inspect a single node’s recent history, health, and metadata.

### 8. Fault Separation
Clearly distinguish:
- real flood concern
- communications problem
- sensor issue
- low-power issue
- maintenance-needed state

### 9. Local Event Persistence
Preserve event history long enough to support post-event review.

---

## Recommended Initial Implementation Posture

The first console should be simple enough to run locally on a laptop or edge machine.

A practical starting posture is:

- lightweight browser-based interface or local desktop-friendly page
- file-backed or simple local-database event store
- manual or mock-data ingest supported early
- easy local startup and reproduction
- no dependence on cloud services for the proof of concept

This keeps the project believable and reproducible.

---

## Core Console Views

The first version of the Local Flood Operations Console should include four primary views.

---

## View 1 — Node Summary View

### Purpose
Provide a fast overview of all active nodes.

### Required Information
Each node entry should show:

- node identifier
- node class
- site name or site label
- current state
- last seen time
- water or trend summary
- power state
- communication state
- maintenance-needed flag
- fault flag if present

### Why This View Matters
A user should be able to open the console and immediately answer:

- which nodes are normal
- which nodes are concerning
- which nodes are questionable
- which nodes are missing

### Suggested Default Sort Order
Prefer one of these default sort approaches:

1. alert severity first
2. maintenance-needed next
3. stale or degraded nodes next
4. normal nodes last

This helps the operator focus.

---

## View 2 — Recent Event History View

### Purpose
Provide a chronological record of significant changes.

### Required Event Types
The view should surface at least these kinds of events:

- state transitions
- communications loss or recovery
- low-power entry
- sensor fault
- maintenance-needed assertion
- maintenance reset or service mark
- alert start
- alert clear

### Required Event Information
Each event should show:

- timestamp
- node identifier
- event type
- previous state if relevant
- new state if relevant
- short human-readable summary

### Why This View Matters
Flood understanding is temporal.

A console that only shows current state hides important context such as:
- which node rose first
- which node went silent before the alert
- whether the event is worsening or recovering

---

## View 3 — Maintenance View

### Purpose
Show which nodes likely need service attention.

### Required Information
The maintenance view should show:

- node identifier
- site
- maintenance-needed flag
- reason for flag if known
- last service date if available
- last seen time
- current state
- most recent relevant maintenance event

### Typical Maintenance Flags
The console should be able to surface flags such as:

- persistent ponding observed
- sensor health degraded
- enclosure humidity high
- repeated invalid reads
- low power recurring
- communications weak or intermittent
- node silent
- self-test failed
- service overdue

### Why This View Matters
The point is not only to watch floods happen.
The point is also to know what should be cleaned, repaired, or inspected before the next event gets worse.

---

## View 4 — Node Detail View

### Purpose
Provide a focused view of one specific node.

### Required Information
The detail view should show:

- node identifier
- node class
- site label
- deployment tier
- current state
- last seen time
- power health
- communication health
- recent state changes
- recent fault events
- maintenance-needed status
- latest available notes or metadata

### Optional Information
If later supported, the detail view may also show:

- sparkline or simple trend graph
- battery voltage history
- signal quality history
- enclosure humidity trend
- service notes

### Why This View Matters
When something looks wrong, the user needs a place to inspect one node without scanning the entire system.

---

## Console State Model

The console should display node states explicitly.

### Core States

#### NORMAL
Conditions appear stable and within expected operating bounds.

#### WATCH
A threshold is approaching or a concerning trend is developing.

#### ALERT
A meaningful flood-related or blockage-related concern is active.

#### DEGRADED
The node is partially useful, but one or more inputs or supports are impaired.

#### FAULT
The node is not trustworthy enough for its intended role.

#### OFFLINE_LOGGING
The node is no longer uplinking but is believed to still be recording events locally.

---

## Required State Display Discipline

The console should never collapse all non-normal conditions into a single vague warning icon.

It must distinguish:

- flood concern
- hardware concern
- visibility concern
- maintenance concern

This is one of the most important believability rules in the entire repository.

---

## Severity Framing

A console may optionally provide a roll-up severity framing for easier scanning.

### Suggested Roll-Up Levels
- low concern
- rising concern
- active concern
- service concern

These labels are optional.

The core explicit node states remain mandatory.

The roll-up is for quick scanning only and should never hide the underlying state.

---

## Data Inputs Expected by the Console

The console should be built around structured node records and event records.

At minimum, it should expect data like:

### Node Status Fields
- node_id
- node_class
- site_label
- current_state
- water_status
- power_state
- communication_state
- maintenance_needed
- fault_code
- last_seen_at
- last_log_at
- firmware_version

### Event Fields
- event_id
- timestamp
- node_id
- event_type
- prior_state
- new_state
- severity
- summary
- source
- acknowledged_flag

The exact schemas can be formalized in later schema files, but the console spec must define the intent clearly.

---

## Console Behavior for Imperfect Data

The console must assume imperfect real-world conditions.

It should handle:

- missing packets
- stale data
- duplicate messages
- nodes that reappear after silence
- delayed event batches
- inconsistent clocks during early prototype stages
- partially complete records

### Console Response Philosophy
The console should degrade gracefully.

It should prefer:
- "stale"
- "delayed"
- "unknown"
- "offline logging suspected"

over fake certainty.

That honesty is part of the project’s credibility.

---

## Required Console Labels and Language Style

The console should use direct operational language.

Preferred wording includes:

- normal
- watch
- alert
- degraded
- fault
- last seen
- maintenance needed
- comms weak
- low power
- stale data
- logging locally

Avoid vague or dramatic wording like:
- crisis mode
- catastrophic
- doom
- severe danger
- red alert maximum
- terminal node state

The interface should support clear action, not drama.

---

## Initial User Roles

The proof-of-concept console does not need a complex permissions model.

But it should recognize three practical user perspectives:

### 1. Builder / Technician
Needs to inspect hardware health, logs, service flags, and node identity.

### 2. Local Operator
Needs to understand which sites are concerning and what changed recently.

### 3. Reviewer / Demonstrator
Needs to understand what the system is showing and whether it is credible.

The first console should remain usable for all three without role-specific account complexity.

---

## Required Filtering and Sorting

The first version should support simple but useful filters.

### Recommended Filters
- by state
- by node class
- by site
- by maintenance-needed flag
- by stale/offline condition

### Recommended Sort Options
- severity
- most recently changed
- last seen
- node identifier
- maintenance priority

This is enough for a serious proof of concept.

---

## Recommended Color and Indicator Logic

The first console should use restrained, legible state coloring.

### Suggested Mapping
- normal = green
- watch = yellow or amber
- alert = red
- degraded = blue or purple
- fault = magenta or distinct dark tone
- stale/offline logging = gray

The exact palette is less important than consistency and contrast.

Color must not be the only indicator.
Text labels must remain visible.

---

## Alert Fatigue Prevention

The console should avoid becoming a noise machine.

### Recommended Early Rules
- do not flood the screen with repeated identical events
- summarize repeated stale conditions when possible
- group recoveries sensibly
- make fault and flood changes visually distinct
- show recent change count where helpful

The point is signal, not spam.

---

## Suggested Basic Screen Layout

A practical proof-of-concept layout can use:

### Top Bar
- project name
- last refresh time
- total node count
- nodes in alert
- nodes degraded or faulted
- nodes needing maintenance

### Main Area Left
- node summary list or table

### Main Area Right
- selected node detail or recent event stream

### Secondary View Tabs
- summary
- events
- maintenance
- node detail

This is enough to be useful without pretending to be a large control center.

---

## Example Interpretive Patterns the Console Should Support

The console should make patterns like these obvious.

### Pattern A — Local Blockage Suspicion
- Smart Inlet Node enters WATCH then ALERT
- nearby Sentinel Node remains NORMAL
- likely interpretation: local drain trouble or local blockage

### Pattern B — Downstream Pressure Problem
- Sentinel Node rises or enters WATCH first
- nearby Smart Inlet Node later enters WATCH or ALERT
- likely interpretation: broader corridor or outfall condition is contributing to poor drainage

### Pattern C — Hardware Trouble
- node enters DEGRADED or FAULT
- communications weaken
- power drops
- no consistent flood trend
- likely interpretation: service needed before trusting the node

### Pattern D — Recovery
- Sentinel trend falls
- Smart Inlet Node exits ALERT to WATCH to NORMAL
- likely interpretation: drainage is recovering

The console does not need to make hard autonomous claims.
It only needs to make these patterns visible.

---

## Logging and Retention Expectations

The console should preserve enough history to support review.

### Minimum Retention Goal
For proof-of-concept use, retain:
- recent node state history
- recent alert history
- recent fault history
- recent maintenance flags
- recent offline/stale events

The exact storage format may be:
- flat files
- JSON lines
- SQLite
- other lightweight local formats

The implementation can stay simple as long as records are readable and exportable.

---

## Export Expectations

A serious proof-of-concept console should make it possible to export useful evidence.

Recommended export targets include:

- node summary snapshot
- recent event history
- maintenance-needed report
- per-node event log
- fault summary

Export can begin as:
- CSV
- JSON
- plain text report

That is enough for pilot review.

---

## Proof-of-Concept Acceptance Criteria

The Local Flood Operations Console should be considered useful if it can do all of the following:

- show all known nodes
- distinguish normal, watch, alert, degraded, and fault states
- show when nodes were last seen
- surface recent changes clearly
- separate likely flood problems from likely hardware problems
- surface maintenance-needed nodes
- stay understandable to a first-time reviewer

If it cannot do those things, it is not ready.

---

## Out-of-Scope Features for the First Version

The first version should **not** chase these features yet:

- advanced mapping stack
- AI-driven forecasting
- fully automatic dispatch
- user account complexity
- remote firmware update control
- giant animated dashboards
- municipal asset command integration
- heavy cloud dependency
- speculative automation beyond the data quality available

Those can wait.

The first version must prove clarity and usefulness first.

---

## Recommended Early Technical Posture

A strong early posture for the console is:

- local-first
- browser-friendly
- lightweight
- file-backed or SQLite-backed
- mock-data friendly
- replay friendly
- export friendly
- tolerant of imperfect timestamps and imperfect connectivity

That keeps the barrier to building and testing low.

---

## Dependencies on Future Repository Files

This console specification should eventually pair with:

- node status schema
- event log schema
- mock data examples
- proof-of-concept test checklist
- operations console implementation notes
- maintenance view examples

The spec defines the target.
Those later files will make it buildable.

---

## Known Limitations of This Specification

This file does not yet define:

- final implementation language
- final UI framework
- final storage engine
- final schema validation stack
- final charting library
- final authentication approach
- final district-scale deployment strategy

That is intentional.

This is a proof-of-concept console specification, not a fully locked software architecture.

---

## Summary

The IX-Bayanihan Local Flood Operations Console is meant to provide:

- clear node visibility
- recent event visibility
- maintenance prioritization
- fault separation
- simple operational interpretation

Its purpose is not to create mythology around the project.

Its purpose is to make the system understandable.

That is enough to make the proof of concept serious.
