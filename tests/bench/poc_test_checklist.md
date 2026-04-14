# IX-Bayanihan Proof-of-Concept Test Checklist

## Purpose

This document defines the baseline test checklist for the **IX-Bayanihan proof of concept**.

It is intended to support disciplined validation of the three proof-of-concept modules:

1. **Smart Inlet Node**
2. **Channel / Outfall Sentinel Node**
3. **Local Flood Operations Console**

The point of this checklist is not to create fake rigor.

The point is to make sure the project can answer basic questions honestly before stronger public claims are made.

This checklist is designed to help builders verify:

- hardware bring-up
- sensor behavior
- local alert behavior
- logging integrity
- degraded-mode behavior
- communications resilience
- outdoor readiness
- interpretability of the console
- maintenance visibility

---

## Scope Boundary

This checklist covers:

- bench tests
- controlled wet tests
- communications and degraded-mode tests
- outdoor dry-run checks
- limited real-condition observation readiness

This checklist does **not** replace:

- professional certification testing
- code compliance inspection
- formal environmental qualification
- lightning qualification
- long-duration lifecycle testing
- municipal acceptance testing

This is a proof-of-concept checklist, not a final validation regime.

---

## Test Philosophy

A useful proof-of-concept test process should prove at least four things:

1. the node can produce meaningful signals
2. the node can fail in understandable ways
3. the logs preserve what happened
4. the operator-facing layer remains interpretable

A weak proof of concept only shows a blinking light.

A serious proof of concept shows **state transitions, evidence retention, and disciplined behavior under imperfect conditions**.

---

## Required Test Conditions

At minimum, the proof of concept should cover:

- baseline dry condition
- threshold crossing
- persistent elevated condition
- recovery condition
- communications loss
- low-power or power-change condition
- invalid sensor condition
- maintenance-needed assertion
- console interpretability under mixed node states

---

## Test Recordkeeping Rule

Every test should capture:

- test identifier
- date
- hardware revision
- firmware revision
- operator or builder name
- module under test
- expected result
- observed result
- pass/fail outcome
- notes
- follow-up action if needed

Do not trust memory alone.

---

# Section 1 — Global Pre-Test Checks

These checks apply before running any module-specific tests.

## 1.1 Documentation Readiness
- [ ] Current BOM file for the module is available
- [ ] Current assembly guidance is available
- [ ] Current firmware or console revision is recorded
- [ ] Current schema version is recorded where applicable
- [ ] Test operator knows which hardware revision is on the bench
- [ ] Node identifier is assigned and labeled

## 1.2 Visual Hardware Inspection
- [ ] Enclosure is intact
- [ ] Wiring is mechanically secure
- [ ] No exposed conductors are present
- [ ] Connectors are seated correctly
- [ ] Sensor mounts are secure
- [ ] Cable glands are tightened appropriately
- [ ] Labels are present and legible
- [ ] No obvious corrosion, cracks, or loose fasteners are visible

## 1.3 Power Safety Check
- [ ] Supply polarity has been confirmed
- [ ] Fuse is installed where expected
- [ ] Battery chemistry matches charge path
- [ ] Power rails are within expected range
- [ ] No unexpected heating is observed on power components
- [ ] Safe shutdown plan exists before energizing the node

## 1.4 Logging Readiness
- [ ] Local storage medium is installed
- [ ] Storage medium is readable
- [ ] Timekeeping source is available or test-time workaround is documented
- [ ] Test log folder or export destination is known
- [ ] Prior logs have been preserved or intentionally cleared

---

# Section 2 — Smart Inlet Node Bench Checklist

## 2.1 Basic Bring-Up
- [ ] Node powers on without obvious fault
- [ ] Boot indicator appears as expected
- [ ] Controller enters expected startup state
- [ ] Storage initialization succeeds
- [ ] Local clock or timestamp source is functioning
- [ ] Node produces a heartbeat or basic status update
- [ ] No repeated boot loop is observed

## 2.2 Baseline Dry-State Behavior
- [ ] Primary water sensor reports a plausible dry or baseline reading
- [ ] Secondary threshold sensor is inactive at dry baseline
- [ ] Node enters or remains in NORMAL state
- [ ] Local status indicator matches NORMAL state
- [ ] Console, if connected, shows the node as healthy and visible
- [ ] Log record confirms stable baseline state

## 2.3 Watch Threshold Simulation
- [ ] Controlled water rise or equivalent simulation is introduced safely
- [ ] Primary sensor reading changes in the expected direction
- [ ] Node enters WATCH at the expected threshold range
- [ ] Watch transition is logged
- [ ] Local status indicator changes correctly
- [ ] Console shows WATCH clearly
- [ ] No false FAULT or DEGRADED state is triggered without reason

## 2.4 Alert Threshold Simulation
- [ ] Water rise or equivalent simulation reaches alert level
- [ ] Node enters ALERT at the expected threshold range
- [ ] Alert transition is logged
- [ ] Local status indicator changes correctly
- [ ] Console shows ALERT clearly
- [ ] Secondary threshold confirmation behaves as expected if installed
- [ ] Alert state remains stable under a steady test condition

## 2.5 Persistent Ponding Simulation
- [ ] Water level is held above normal for the planned persistence duration
- [ ] Node remains in the correct active state without oscillation
- [ ] Maintenance-needed or blockage-related logic behaves as designed
- [ ] Persistent condition is logged with usable detail
- [ ] Console surfaces the condition clearly
- [ ] No unexplained resets occur during hold time

## 2.6 Recovery Simulation
- [ ] Water condition is reduced safely
- [ ] Node exits ALERT and/or WATCH correctly
- [ ] Recovery is logged
- [ ] Local indicator returns to appropriate post-event state
- [ ] Console reflects recovery clearly
- [ ] No stale alert remains active without reason

## 2.7 Sensor Fault Simulation
- [ ] Primary sensor is disconnected, blocked, spoofed, or otherwise invalidated safely
- [ ] Node detects the abnormal condition
- [ ] Node enters DEGRADED or FAULT as designed
- [ ] Fault is logged
- [ ] Console clearly distinguishes hardware trouble from a flood alert
- [ ] If a secondary threshold exists, its behavior remains interpretable

## 2.8 Power Variation Check
- [ ] Input voltage is reduced within a safe test window or alternate power source is switched
- [ ] Node reports battery or power-state changes correctly
- [ ] Low-power condition is logged if threshold is crossed
- [ ] Node remains stable or enters expected degraded mode
- [ ] Node recovers cleanly when stable power returns
- [ ] Brownout recovery, if triggered, is logged

---

# Section 3 — Channel / Outfall Sentinel Bench Checklist

## 3.1 Basic Bring-Up
- [ ] Sentinel node powers on correctly
- [ ] Boot state and heartbeat are visible
- [ ] Storage initialization succeeds
- [ ] Communications module initializes as expected
- [ ] Sensor reading is plausible at dry baseline
- [ ] Local visible status is working
- [ ] No repeated reset behavior is observed

## 3.2 Baseline Dry-State Behavior
- [ ] Node enters or remains in NORMAL state under baseline condition
- [ ] Water-status summary is reasonable
- [ ] Console shows node as visible and healthy
- [ ] Event log includes a stable baseline record

## 3.3 Rising-Water Trend Simulation
- [ ] Controlled level increase or equivalent simulation is introduced safely
- [ ] Primary sensor tracks change in the expected direction
- [ ] Node enters WATCH appropriately
- [ ] Trend classification is plausible
- [ ] Event log records the trend change clearly
- [ ] Console shows the sentinel state change distinctly

## 3.4 Alert-Level Simulation
- [ ] Simulated level crosses planned alert condition
- [ ] Node enters ALERT appropriately
- [ ] Alert record is logged
- [ ] Local visible indicator changes correctly
- [ ] Console shows the alert clearly
- [ ] Secondary threshold confirmation behaves correctly if installed

## 3.5 Communications Loss Simulation
- [ ] Communications path is interrupted safely
- [ ] Node enters OFFLINE_LOGGING or equivalent state if designed
- [ ] Local logging continues
- [ ] Console marks the node as stale, delayed, or offline appropriately
- [ ] No fake “healthy online” state persists during the outage
- [ ] Restored communications do not destroy local logs

## 3.6 Sensor Occlusion or Splash-Equivalent Check
- [ ] Sensor face is safely obstructed or disturbed in a controlled way
- [ ] Node detects suspect readings or degraded conditions appropriately
- [ ] False flood claims are avoided where possible
- [ ] Degraded or fault record is logged
- [ ] Console separates the sensor issue from true alert conditions

## 3.7 Power Behavior Check
- [ ] Battery or alternate supply is tested as applicable
- [ ] Low-power reporting works
- [ ] Node remains stable or degrades gracefully
- [ ] Recovery after stable power return is clean
- [ ] Event records remain usable

---

# Section 4 — Local Flood Operations Console Checklist

## 4.1 Startup and Access
- [ ] Console starts successfully
- [ ] Mock or live data source is reachable
- [ ] Summary view loads without error
- [ ] No mandatory cloud dependency blocks local use
- [ ] Operator can identify active nodes quickly

## 4.2 Summary View
- [ ] Node list displays correctly
- [ ] Current state is visible for each node
- [ ] Last-seen time is visible
- [ ] Maintenance-needed indicator is visible
- [ ] Faulted and degraded nodes are visibly distinct from alert nodes
- [ ] Sorting by severity or recent change works as intended

## 4.3 Event History View
- [ ] Recent events appear in time order
- [ ] State transitions are readable
- [ ] Flood-condition events and hardware-fault events are distinguishable
- [ ] Event summaries are short but understandable
- [ ] Missing or delayed data is handled without UI collapse

## 4.4 Maintenance View
- [ ] Maintenance-needed nodes can be filtered or viewed directly
- [ ] Maintenance reason is shown when available
- [ ] Last service date is shown when available
- [ ] Stale or silent nodes are identifiable for inspection triage

## 4.5 Node Detail View
- [ ] Individual node details can be opened
- [ ] Current state and recent history are visible
- [ ] Power and communication health are visible
- [ ] Latest meaningful event is accessible
- [ ] Node identity and class are clearly labeled

## 4.6 Mixed-State Interpretability
- [ ] Console can display at least one NORMAL node and one ALERT node at the same time clearly
- [ ] Console can display a FAULT node without confusing it with flood conditions
- [ ] Console can display an OFFLINE or stale node clearly
- [ ] First-time reviewer can understand what is happening quickly

---

# Section 5 — Controlled Wet Test Checklist

This section applies to wet but controlled testing for the node modules.

## 5.1 Wet Test Safety
- [ ] Test water is introduced in a controlled environment
- [ ] No energized mains equipment is exposed to water
- [ ] Builder can stop the test quickly if something fails
- [ ] Towels, drying materials, and safe cleanup tools are available
- [ ] Test area drainage is understood
- [ ] Electrical contacts are protected from accidental splash where required

## 5.2 Repeatability
- [ ] Starting water level is documented
- [ ] Test duration is documented
- [ ] Threshold targets are documented
- [ ] Each repeated run uses the same intended geometry as closely as practical
- [ ] Differences between runs are recorded

## 5.3 Log Verification
- [ ] Water rise events were logged
- [ ] Watch/alert transitions were logged
- [ ] Recovery transitions were logged
- [ ] Faults or anomalies during wet test were logged
- [ ] Timestamps are plausible and ordered correctly
- [ ] Event records can be exported or reviewed later

## 5.4 Post-Wet Inspection
- [ ] Enclosure exterior is inspected
- [ ] No unintended water ingress is observed
- [ ] Sensors remain mounted correctly
- [ ] Wiring remains secure
- [ ] Connectors remain seated
- [ ] Local indicators still work
- [ ] Any moisture, drift, or looseness is recorded

---

# Section 6 — Communications and Degraded-Mode Checklist

## 6.1 Communications Interruption
- [ ] Uplink can be interrupted safely
- [ ] Node behavior under loss is predictable
- [ ] Console marks staleness correctly
- [ ] Node preserves local logs if designed to do so
- [ ] Recovery after reconnection is understandable

## 6.2 Local Logging While Offline
- [ ] Important state changes continue to be recorded locally
- [ ] Local log remains readable after reconnection
- [ ] No obvious duplicate corruption appears during delayed sync or manual retrieval
- [ ] Offline logging state is visible in logs or console if supported

## 6.3 Degraded-Mode Truthfulness
- [ ] Node does not continue claiming NORMAL when a critical subsystem is impaired
- [ ] DEGRADED and FAULT are used consistently
- [ ] Console does not hide degraded or missing data
- [ ] Human reviewer can still interpret what happened

---

# Section 7 — Outdoor Dry-Run Checklist

The outdoor dry run is not a full flood event.
It is a survivability and practicality check.

## 7.1 Installation Practicality
- [ ] Mount point is reachable safely
- [ ] Enclosure can be secured properly
- [ ] Sensor orientation can be set and checked
- [ ] Cables can be routed without obvious hazard
- [ ] Labels remain visible after mounting
- [ ] Module does not obstruct drainage or create a trip hazard

## 7.2 Environmental Readiness
- [ ] Enclosure remains closed and stable
- [ ] Heat buildup is acceptable
- [ ] Condensation is not immediately visible inside the enclosure
- [ ] Communications path is usable at the chosen site
- [ ] Solar input is plausible if solar is part of the design
- [ ] Local indicator remains visible in outdoor lighting

## 7.3 Serviceability
- [ ] Builder can access the node again without unusual tools
- [ ] Enclosure can be opened and closed cleanly
- [ ] Sensor can be inspected without damaging the mount
- [ ] Node can be removed or replaced without site damage
- [ ] Service notes are recorded

---

# Section 8 — Real-Condition Observation Checklist

This section is for safe observation during real rain or runoff conditions.

## 8.1 Safety Boundary
- [ ] No one enters dangerous floodwater
- [ ] No one stands in unsafe traffic exposure
- [ ] No one leans into a dangerous channel edge
- [ ] Test observers have an exit plan
- [ ] Observation remains within lawful and safe site access

## 8.2 Data Usefulness
- [ ] Node captured state changes during real conditions
- [ ] Local visible status matched observed conditions
- [ ] Console showed a coherent progression
- [ ] Logs were preserved
- [ ] Builder recorded visual site notes for later comparison
- [ ] False positives and false negatives are recorded honestly

## 8.3 Post-Event Review
- [ ] Logs have been retrieved
- [ ] Timeline of events has been reconstructed
- [ ] Sensor behavior is compared with observed site conditions
- [ ] Unclear events are tagged for review
- [ ] Maintenance or redesign needs are documented

---

# Section 9 — Pass / Needs Work Decision Rules

A module or console component should be considered **passable for the next stage** only if:

- [ ] it behaves predictably under normal conditions
- [ ] it enters WATCH and ALERT in a repeatable way
- [ ] it handles at least one degraded or fault condition honestly
- [ ] it logs meaningful events
- [ ] a reviewer can reconstruct what happened
- [ ] service or maintenance needs are understandable
- [ ] it does not rely on hand-waving to explain failures

A module or console component should be considered **needs work** if:

- [ ] thresholds are unstable or unexplained
- [ ] logs are incomplete or confusing
- [ ] the console confuses faults with floods
- [ ] the node fails silently
- [ ] the node is impractical to mount or service
- [ ] power behavior is unstable
- [ ] no actionable lesson is produced

---

# Section 10 — Minimum Test Artifacts to Preserve

At the end of each proof-of-concept test cycle, preserve:

- [ ] completed checklist copy
- [ ] hardware revision note
- [ ] firmware revision note
- [ ] test photos if lawful and safe
- [ ] exported node status samples
- [ ] exported event logs
- [ ] observed issues list
- [ ] next-step revision list

These artifacts are part of the credibility of the project.

---

## Summary

This checklist exists to keep **IX-Bayanihan** honest.

A believable proof of concept must show:

- disciplined hardware behavior
- useful logs
- clear state transitions
- visible degraded-mode handling
- understandable operator output
- actionable maintenance insight

That is the standard.

Anything weaker may still be interesting, but it is not yet serious enough to claim meaningful flood-support value.
