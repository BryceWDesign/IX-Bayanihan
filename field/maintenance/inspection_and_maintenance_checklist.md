# IX-Bayanihan Inspection and Maintenance Checklist

## Purpose

This document defines the baseline inspection and maintenance checklist for **IX-Bayanihan** field hardware.

It is intended to support disciplined upkeep of:

- Smart Inlet Nodes
- Channel / Outfall Sentinel Nodes
- future gateway or relay hardware if later added

The purpose of this checklist is simple:

> **A flood-support node that cannot be maintained will eventually become a liar.**

If the hardware is dirty, misaligned, water-damaged, low on power, partially clogged, or silently degraded, the system can begin producing misleading outputs.

This checklist exists to reduce that risk.

---

## Scope Boundary

This checklist is for:

- routine inspection
- post-rain inspection
- post-fault inspection
- battery and power review
- enclosure and sealing review
- sensor cleaning
- mount integrity checks
- log retrieval and maintenance recordkeeping
- proof-of-concept and pilot deployments

This checklist does **not** replace:

- formal municipal maintenance programs
- structural inspection by licensed professionals
- electrical code inspection
- confined-space procedures
- stormwater infrastructure maintenance authority
- legal access requirements
- hazardous-weather field rules

This is a repository-level field discipline document.

---

## Maintenance Philosophy

IX-Bayanihan follows six maintenance rules.

### Rule 1: Service Before Failure Matters More Than Heroics After Failure
If a node is easy to inspect and maintain, it stays useful longer.

### Rule 2: Dirty Sensors Lie
A blocked, splashed, buried, or fouled sensor may still output numbers.
That does not mean those numbers are trustworthy.

### Rule 3: Logs Are Part of Maintenance
Cleaning the hardware but ignoring the fault history misses half the picture.

### Rule 4: Repeat Trouble Spots Are Signal, Not Noise
If one site repeatedly needs service, that is information about the site, not just the hardware.

### Rule 5: Seals and Mounts Are Part of the Measurement System
A loose mount or failing gasket is not cosmetic.
It directly affects trust.

### Rule 6: Maintenance Records Must Outlive Memory
A node with no service history becomes harder to trust and harder to improve.

---

## Inspection Frequency Guidance

Inspection timing depends on deployment tier and site harshness.

### Suggested Baseline Rhythm

#### Bench or controlled proof-of-concept units
- inspect before each major test session
- inspect after each wet test

#### Tier 2 field pilots
- inspect shortly after first deployment
- inspect after meaningful rain events
- inspect after any communications silence or unexplained degraded state
- inspect on a regular interval appropriate to exposure

#### Tier 3 hardened community nodes
- inspect on a regular service schedule
- inspect after major weather events
- inspect after any major fault or suspected ingress event
- inspect when maintenance-needed flags persist

This repository does not force one fixed interval because site conditions vary widely.

---

## Required Maintenance Record

Every inspection or maintenance action should record at minimum:

- date
- node ID
- node class
- site label
- inspector or team name
- reason for visit
- current node state before service
- visible site condition
- actions taken
- parts replaced if any
- logs reviewed or retrieved
- open issues
- next recommended inspection date

Without this record, later troubleshooting becomes much weaker.

---

# Section 1 — Pre-Inspection Readiness

## 1.1 Documentation Readiness
- [ ] Node ID is known
- [ ] Site label is known
- [ ] Hardware revision is known
- [ ] Latest firmware version is known if applicable
- [ ] Last service date is available
- [ ] Prior unresolved issues are reviewed before visiting the site

## 1.2 Safety Readiness
- [ ] Site can be accessed safely at current conditions
- [ ] Team will not enter dangerous floodwater
- [ ] Team will not work in unsafe traffic exposure
- [ ] Team will not access unauthorized or unsafe infrastructure
- [ ] Service tools are appropriate to the node type
- [ ] Weather conditions are acceptable for safe inspection

## 1.3 Service Kit Readiness
- [ ] Correct screwdrivers / keys / tools are packed
- [ ] Cleaning materials are packed
- [ ] Spare fuses are packed if relevant
- [ ] Spare cable glands or seals are packed if relevant
- [ ] Spare sensor or connector components are packed if relevant
- [ ] Log retrieval method is available if required
- [ ] Labels or maintenance tags are available if needed

---

# Section 2 — Initial On-Site Observation

Before touching the node, observe the site as it currently exists.

## 2.1 General Site Condition
- [ ] Standing water present or absent is noted
- [ ] Debris load at or near the site is noted
- [ ] Visible sediment accumulation is noted
- [ ] Blockage suspicion at the drain, inlet, channel, or outfall is noted
- [ ] Signs of backflow or prolonged ponding are noted if present
- [ ] Any new physical hazards are noted

## 2.2 Node Exterior Observation
- [ ] Enclosure appears intact
- [ ] Mount appears stable
- [ ] Sensor orientation appears unchanged
- [ ] External labels are still readable
- [ ] Cables appear intact
- [ ] Cable glands appear intact
- [ ] Antenna appears intact if present
- [ ] Splash guard or hood appears intact if present

## 2.3 Visible Damage Check
- [ ] No obvious impact damage
- [ ] No obvious vandalism or tampering
- [ ] No obvious crack in enclosure
- [ ] No obvious missing fasteners
- [ ] No obvious exposed conductor
- [ ] No obvious broken sensor bracket
- [ ] No obvious severe corrosion beyond expected minor surface aging

---

# Section 3 — Smart Inlet Node Inspection Checklist

Use this section when inspecting a Smart Inlet Node.

## 3.1 Site Function Check
- [ ] The monitored inlet or drain is still relevant to flood behavior
- [ ] The node is not obstructing drainage
- [ ] The monitored zone is still visible to the sensor
- [ ] The site has not changed in a way that invalidates the sensor target

## 3.2 Local Debris and Sediment Check
- [ ] Trash accumulation near the inlet is noted
- [ ] Sediment accumulation near the sensor target is noted
- [ ] Bio-growth or slime affecting the sensing path is noted
- [ ] Splash contamination on the sensor face or shield is noted

## 3.3 Sensor Condition
- [ ] Primary sensor face is visually inspected
- [ ] Primary sensor is cleaned if required
- [ ] Secondary threshold sensor is inspected if present
- [ ] Sensor cable strain is checked
- [ ] Sensor mounting remains secure
- [ ] Sensor alignment remains useful

## 3.4 Local Indicator Check
- [ ] LED or beacon remains visible
- [ ] Indicator lens or window is clean enough to read
- [ ] Indicator hardware is physically secure
- [ ] Indicator behavior can be verified if the node is energized

## 3.5 Site Interpretation Note
- [ ] Inspector records whether the site suggests local blockage, persistent ponding, or normal recovery behavior
- [ ] Inspector notes whether repeated maintenance at this site appears to indicate a real drainage pain point rather than a node-only issue

---

# Section 4 — Sentinel Node Inspection Checklist

Use this section when inspecting a Channel / Outfall Sentinel Node.

## 4.1 Corridor Visibility Check
- [ ] The sensor still has line of sight to the intended water target zone
- [ ] New obstructions such as debris, vegetation, or structural changes are noted
- [ ] The node still observes meaningful corridor behavior rather than a useless surface

## 4.2 Exposed-Environment Condition Check
- [ ] Splash contamination is checked
- [ ] Mud, sediment, or salt residue is checked
- [ ] Bird fouling or organic contamination is checked
- [ ] Biofouling on sensor housing or shield is checked
- [ ] Corrosion on external hardware is checked

## 4.3 Mount and Aim Check
- [ ] External bracket remains stable
- [ ] Sensor aim bracket remains stable
- [ ] Sensor aim still points to the intended measurement region
- [ ] No twist, sag, or vibration-induced drift is observed
- [ ] Tightening or realignment is performed if needed

## 4.4 Optional Camera or Auxiliary Check
If the node includes optional visual hardware:
- [ ] Viewport is clean enough to remain useful
- [ ] Camera module appears intact
- [ ] Camera mounting has not loosened
- [ ] Camera path is not blocked by grime or interior condensation

## 4.5 Site Interpretation Note
- [ ] Inspector records whether the corridor shows signs of elevated downstream pressure, backflow, or recurring high-water behavior
- [ ] Inspector notes whether the node still provides useful context beyond nearby street nodes

---

# Section 5 — Enclosure Inspection Checklist

These checks apply to all node classes.

## 5.1 Exterior Enclosure Condition
- [ ] Enclosure body has no serious cracks
- [ ] Lid seats correctly
- [ ] Fasteners are present and secure
- [ ] Cable glands are tight and undamaged
- [ ] No obvious water-track pattern into the enclosure is visible from outside

## 5.2 Controlled Opening Check
When safe and appropriate:
- [ ] Enclosure is opened carefully
- [ ] Gasket path is inspected
- [ ] No pooled water is found inside
- [ ] No heavy condensation is found inside
- [ ] No corrosion is found on internal terminals beyond minor surface signs
- [ ] No loose hardware is found inside
- [ ] No insect, nest, or foreign debris intrusion is found inside

## 5.3 Interior Hardware Condition
- [ ] Controller mount remains secure
- [ ] Storage module remains secure
- [ ] Battery remains secured
- [ ] Connectors remain seated
- [ ] No wire insulation damage is visible
- [ ] No cable pinch damage is visible
- [ ] No abnormal heat discoloration is visible
- [ ] Service labels remain readable

## 5.4 Resealing Check
After inspection:
- [ ] Gasket path is cleaned
- [ ] Lid is reseated correctly
- [ ] Fasteners are tightened evenly
- [ ] Cable glands remain correctly tightened
- [ ] Enclosure is restored to weather-ready state

---

# Section 6 — Power System Inspection Checklist

## 6.1 Battery Condition
- [ ] Battery is physically secure
- [ ] No swelling, cracking, or leakage is observed
- [ ] Terminal condition appears acceptable
- [ ] Battery voltage is checked if appropriate
- [ ] Battery state aligns reasonably with recent weather and runtime expectations

## 6.2 Charging Path Check
If solar or other charging is used:
- [ ] Panel appears intact
- [ ] Panel mounting appears stable
- [ ] Panel cable route appears intact
- [ ] Charge controller appears healthy
- [ ] Charging behavior, if observable, is plausible
- [ ] No obvious connector corrosion is present in the charging path

## 6.3 Power Protection Check
- [ ] Fuse is present
- [ ] Fuse rating matches expected documentation
- [ ] Reverse-polarity protection path remains intact as designed
- [ ] Surge or transient protection components show no obvious damage if inspectable

## 6.4 Power Interpretation Note
- [ ] Inspector records whether the node’s recent power behavior suggests battery sizing, charging, or power-budget problems
- [ ] Inspector records whether power issues may explain recent degraded or fault states

---

# Section 7 — Communications and Logging Inspection Checklist

## 7.1 Communications Hardware Check
- [ ] Radio module remains physically secure
- [ ] Antenna remains connected
- [ ] Antenna mount remains stable
- [ ] No obvious cable or connector damage is present
- [ ] No obvious enclosure change is blocking antenna function

## 7.2 Communications Behavior Check
Where practical:
- [ ] Heartbeat or status signal is observed
- [ ] Last-seen timing is reviewed
- [ ] Repeated communications dropouts are noted
- [ ] Communications behavior remains plausible for the site

## 7.3 Local Logging Check
- [ ] Storage medium is present
- [ ] Local logs can be read or retrieved if needed
- [ ] Recent events appear plausible
- [ ] No obvious storage corruption is seen
- [ ] Timestamp quality is acceptable
- [ ] Offline logging capability, if supported, appears to have worked as expected

## 7.4 Log Review Questions
During maintenance, ask:
- [ ] Did the node record unexplained resets?
- [ ] Did the node enter DEGRADED or FAULT repeatedly?
- [ ] Did maintenance-needed flags appear repeatedly?
- [ ] Did power-related events correlate with performance issues?
- [ ] Did communications problems hide useful flood-related events?

---

# Section 8 — Functional Spot Check

A maintenance visit should include a simple truthfulness check where safe and practical.

## 8.1 Node Identity Check
- [ ] Node ID on hardware matches records
- [ ] Site label matches records
- [ ] Hardware revision matches records if visible

## 8.2 Live-State Check
- [ ] Current node state is observed
- [ ] Local indicator matches the known state logic
- [ ] Current state is plausible for site conditions
- [ ] No obvious mismatch exists between visible site condition and node state

## 8.3 Fault Truthfulness Check
- [ ] If the node is degraded or faulted, the likely reason is understandable
- [ ] If the node claims normal, the inspector agrees the node appears healthy enough for that claim
- [ ] If the node claims alert, the site gives at least plausible supporting context or the issue is documented for later review

This is not about proving perfection.
It is about detecting obvious lies early.

---

# Section 9 — Cleaning and Corrective Action Checklist

## 9.1 Cleaning Actions
As needed:
- [ ] Sensor face cleaned
- [ ] Splash guard cleaned
- [ ] Indicator window cleaned
- [ ] Enclosure exterior cleaned enough for inspection
- [ ] Debris removed from around node without creating site damage
- [ ] Minor sediment removed where it directly degrades sensing

## 9.2 Tightening and Repositioning
As needed:
- [ ] Loose fasteners retightened
- [ ] Sensor aim corrected
- [ ] Mount alignment corrected
- [ ] Cable slack corrected
- [ ] Antenna repositioned if needed
- [ ] Internal loose hardware corrected

## 9.3 Minor Replacement Actions
As needed:
- [ ] Fuse replaced
- [ ] Cable gland replaced
- [ ] Label replaced
- [ ] Connector re-terminated
- [ ] Secondary sensor replaced
- [ ] SD card replaced
- [ ] Battery replaced if required and documented

## 9.4 Corrective Action Boundary
Do **not** improvise major redesigns at the site unless that is part of a documented service plan.

If the node needs redesign rather than simple service:
- document the issue
- restore the node to a safe state if possible
- record the unit as needing engineering revision

---

# Section 10 — Post-Rain or Post-Event Inspection Checklist

Use this section after a meaningful rain, runoff, or flood-related event.

## 10.1 Site Outcome Check
- [ ] Inspector notes visible signs of ponding, flow marks, trash movement, or backflow evidence
- [ ] Inspector notes whether site behavior matched node-reported concerns
- [ ] Inspector notes any mismatch between logs and visible aftermath

## 10.2 Node Survivability Check
- [ ] Mount survived event
- [ ] Enclosure survived event
- [ ] Sensor remained aligned
- [ ] Node continued logging or communications as expected
- [ ] No major ingress or physical strike damage is present

## 10.3 Evidence Retrieval
- [ ] Relevant logs are retrieved
- [ ] Key event timeline is reviewed
- [ ] Faults during event are noted
- [ ] Maintenance-needed flags during event are noted
- [ ] Lessons learned are recorded

---

# Section 11 — Maintenance Rejection Conditions

A node should be marked **needs major revision**, **needs removal**, or **not trustworthy until repaired** if any of the following are true:

- [ ] enclosure has serious ingress
- [ ] sensor line of sight is no longer valid
- [ ] mount is unstable
- [ ] repeated unexplained resets continue
- [ ] logs are corrupted or missing repeatedly
- [ ] power system is unsafe or unstable
- [ ] the node’s state behavior is no longer believable
- [ ] the node cannot be serviced safely at its current location
- [ ] corrosion or physical damage exceeds minor field-correctable condition

Marking a node as untrustworthy is part of honest maintenance, not a failure of discipline.

---

# Section 12 — Inspection Outcome Summary

At the end of the visit, classify the node as one of the following:

## 12.1 Acceptable
Use when:
- node remains trustworthy
- any issues were minor
- no major revision is needed

## 12.2 Acceptable with Follow-Up Needed
Use when:
- node still works
- one or more issues need near-term attention
- data may remain useful but service should not be delayed

## 12.3 Needs Repair Before Trusting
Use when:
- the node still exists physically
- but its readings or logs should not currently be trusted

## 12.4 Needs Removal or Redesign
Use when:
- the site, mount, enclosure, sensor geometry, or power design no longer supports believable operation

Record the outcome clearly.

---

# Section 13 — Minimum Maintenance Record to Preserve

After each visit, preserve at minimum:

- completed checklist copy
- date
- node ID
- service outcome classification
- actions taken
- parts replaced
- photos or sketches if lawful and useful
- log export or note that logs were reviewed
- next recommended inspection date
- redesign notes if needed

These records should stay with the project history.

---

## Summary

This checklist exists to keep **IX-Bayanihan** honest after deployment.

A believable flood-support node is not just something you build once.

It is something you:

- inspect
- clean
- verify
- document
- correct
- and sometimes pull back when it stops being trustworthy

That is the maintenance standard this repository should uphold.
