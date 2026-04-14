# IX-Bayanihan Field Deployment Checklist

## Purpose

This document defines the baseline field deployment checklist for **IX-Bayanihan** proof-of-concept and pilot hardware.

The purpose of this checklist is to make deployment disciplined, repeatable, and honest.

It is intended for use when placing:

- Smart Inlet Nodes
- Channel / Outfall Sentinel Nodes
- early gateway or relay hardware if later added

This checklist helps builders and field teams verify that a node is:

- ready to install
- appropriate for the site
- physically safe to place
- electrically safe to energize
- understandable to service later
- documented well enough to trust its future data

This is not bureaucracy for its own sake.

A flood-support project becomes untrustworthy very quickly when deployed nodes have no clean site record, no safe service path, and no repeatable deployment method.

---

## Scope Boundary

This checklist is for:

- proof-of-concept deployment
- field pilot deployment
- short-term outdoor placement
- early community demonstration deployments
- non-life-critical open flood-support hardware

This checklist does **not** replace:

- local permits
- utility clearances
- structural engineering review
- environmental approvals
- public works authorization
- confined-space procedures
- energized public-infrastructure work procedures
- traffic-control planning
- formal municipal deployment protocols

If a site requires formal authority, this checklist does not override that requirement.

---

## Deployment Philosophy

A node should only be deployed if all three of these are true:

1. it is technically ready
2. the site is appropriate
3. the team can service it safely later

A deployment that cannot be serviced is a bad deployment.

A deployment with poor site reasoning is a bad deployment.

A deployment with weak documentation is a bad deployment.

---

## Required Deployment Record

Before a node is left in the field, the deployment record should include at minimum:

- deployment date
- node ID
- node class
- hardware revision
- firmware version
- deployment tier
- site label
- site description
- installer or team name
- mounting method
- power method
- communications method
- intended sensing target
- known risks
- photos or sketches if lawful and appropriate
- next inspection date

This record is part of the node’s credibility.

---

# Section 1 — Pre-Deployment Readiness

## 1.1 Documentation Readiness
- [ ] Current BOM exists for the deployed module
- [ ] Current assembly walkthrough exists
- [ ] Current test checklist has been completed or updated for this unit
- [ ] Hardware revision is recorded
- [ ] Firmware version is recorded
- [ ] Node ID is assigned and physically labeled
- [ ] Deployment record form is prepared

## 1.2 Technical Readiness
- [ ] Node boots reliably
- [ ] Local status indicator works
- [ ] Local event logging works
- [ ] Sensor readings are plausible in dry baseline conditions
- [ ] Power monitoring works
- [ ] Communications behavior has been checked
- [ ] Fault behavior has been checked at least once in controlled conditions
- [ ] Enclosure can be opened and closed cleanly
- [ ] No known unresolved electrical instability remains

## 1.3 Physical Inspection Before Leaving the Bench
- [ ] Enclosure gasket is intact
- [ ] Cable glands are installed and tightened correctly
- [ ] Fasteners are tight
- [ ] Sensor mount is secure
- [ ] External bracket hardware is present
- [ ] Labels are legible
- [ ] Storage medium is installed if used
- [ ] Battery is secured
- [ ] No loose hardware is inside the enclosure
- [ ] No exposed conductors are visible

---

# Section 2 — Site Selection Checklist

## 2.1 Site Relevance
- [ ] The site has real flood relevance
- [ ] The site is known or suspected to experience drainage trouble, rising water, backflow, or recurring blockage
- [ ] The site teaches something useful if monitored
- [ ] The site aligns with the node class being deployed

## 2.2 Smart Inlet Node Site Fit
For Smart Inlet Nodes, confirm:
- [ ] the selected inlet, drain, sump edge, or low point actually experiences ponding or slow drainage
- [ ] the node can observe the relevant water behavior
- [ ] the node will not obstruct drainage
- [ ] the node will not be placed directly in the heaviest trash strike path unless that is intentional and safe

## 2.3 Sentinel Node Site Fit
For Sentinel Nodes, confirm:
- [ ] the site has a clear target water-surface zone
- [ ] the sensor can observe useful broader corridor behavior
- [ ] the node can help explain downstream or channel conditions, not just duplicate a street-node reading
- [ ] the mounting position is not in an obvious heavy-impact debris path

## 2.4 Legal and Access Fit
- [ ] The team has lawful access to the site
- [ ] The team is not attaching hardware to protected infrastructure without authorization
- [ ] The site does not require a permit the team lacks
- [ ] The team understands who controls the site if follow-up service is needed

## 2.5 Safety Fit
- [ ] The site can be accessed without entering dangerous water
- [ ] The site can be accessed without unsafe road exposure
- [ ] The site does not require improvised climbing or leaning into a dangerous channel
- [ ] The site has a safe approach path
- [ ] The site has a safe exit path if weather worsens

---

# Section 3 — Site Hazard Review

## 3.1 Electrical and Utility Hazards
- [ ] No unsafe contact with mains wiring is required
- [ ] No overhead or buried utility hazard has been ignored
- [ ] No deployment step requires energized public equipment contact
- [ ] The node’s power method is appropriate for the site

## 3.2 Water and Access Hazards
- [ ] The team is not entering confined drains, manholes, or culverts
- [ ] The team is not stepping into unstable mud, submerged edges, or unknown footing
- [ ] The team is not exposing themselves to sudden runoff without escape planning
- [ ] The team is not deploying during conditions beyond the team’s safe capability

## 3.3 Traffic and Public Interaction Hazards
- [ ] The node does not create a pedestrian trip hazard
- [ ] The node does not create a cyclist or vehicle hazard
- [ ] The team is visible enough if working near a roadway
- [ ] The installation does not invite dangerous tampering by the public
- [ ] The team has a plan for handling questions or site interruption safely

## 3.4 Environmental Hazards
- [ ] Expected splash, debris, heat, humidity, and UV exposure have been considered
- [ ] The node is not placed where immediate burial by sediment is obvious
- [ ] The node is not placed where constant heavy trash impact will destroy it immediately
- [ ] The enclosure and mount materials fit the exposure level

---

# Section 4 — Mounting and Physical Placement Checklist

## 4.1 Mount Geometry
- [ ] The mount type matches the site condition
- [ ] The enclosure is physically stable
- [ ] The node does not wobble under light hand-check
- [ ] The mount does not rely on weak ad hoc fastening
- [ ] The sensor aim is stable

## 4.2 Sensor Sightline or Sensing Path
- [ ] The primary sensor has a useful target zone
- [ ] There is no obvious blind obstruction
- [ ] The sensor is not aimed at a meaningless surface
- [ ] The sensor is not aimed into a geometry likely to generate constant false readings
- [ ] The sensing path can be inspected later

## 4.3 Service Access
- [ ] The enclosure can be reached again safely
- [ ] The enclosure can be opened again without removing major site hardware unnecessarily
- [ ] The sensor can be cleaned or inspected later
- [ ] The battery or serviceable internals can be reached later
- [ ] The node can be removed or replaced if needed

## 4.4 Public and Environmental Fit
- [ ] The node does not obstruct flow
- [ ] The node does not block routine maintenance by local crews
- [ ] The node is not placed where it will obviously collect dangerous debris around itself
- [ ] The node does not create a snag point or entanglement hazard

---

# Section 5 — Power and Communications Deployment Checklist

## 5.1 Power Readiness
- [ ] Battery is connected correctly
- [ ] Fuse is installed
- [ ] Reverse-polarity protection is present as designed
- [ ] Battery condition is acceptable before deployment
- [ ] Solar input is realistic for the site if solar is used
- [ ] Power cables are secured and strain-relieved
- [ ] No exposed low-voltage wiring is left vulnerable

## 5.2 Site Power Fit
- [ ] The power subsystem fits expected weather exposure
- [ ] The node does not depend on an unsafe temporary power arrangement
- [ ] The battery is not placed where water pooling is likely to sit directly against connectors
- [ ] The enclosure orientation supports water shedding rather than water collection

## 5.3 Communications Check
- [ ] Basic communications are working at the site or were tested immediately before final mounting
- [ ] Antenna is installed correctly
- [ ] Communications weakness at the site is understood and recorded
- [ ] Offline logging is confirmed if the communications link is weak or intermittent
- [ ] The team knows how logs will be retrieved if communications fail

---

# Section 6 — Enclosure and Sealing Checklist

## 6.1 Closure Integrity
- [ ] Lid is fully seated
- [ ] Gasket path is clean
- [ ] Lid fasteners are tightened evenly
- [ ] No wire is pinched across the seal path
- [ ] Cable glands grip the cable jacket correctly
- [ ] Beacon or indicator penetrations are sealed correctly
- [ ] Antenna penetration is sealed correctly if external

## 6.2 Weather Readiness
- [ ] The enclosure orientation reduces water pooling risk
- [ ] Open penetrations are not facing upward without protection
- [ ] Sensor hood or splash guard is present if required
- [ ] The node is not obviously vulnerable to the first routine rain splash

---

# Section 7 — Final On-Site Functional Check

## 7.1 Baseline Functional Check
- [ ] Node powers on or remains powered correctly on site
- [ ] Local status indicator is visible
- [ ] The baseline dry or low-water reading is plausible on site
- [ ] No immediate fault state appears without explanation
- [ ] No repeated reset behavior appears

## 7.2 Communications Functional Check
- [ ] Node heartbeat or initial message is seen if communications are expected
- [ ] Last-seen state is updated in the console if available
- [ ] If communications are weak, the deployment record notes that fact clearly

## 7.3 Logging Functional Check
- [ ] At least one post-deployment event is logged
- [ ] Timekeeping appears plausible
- [ ] The team knows how to retrieve the log later if needed

## 7.4 Indicator Interpretation Check
- [ ] The team confirms what each local indicator state means
- [ ] The team confirms the node label is readable
- [ ] The team confirms that a future maintainer can interpret the node without tribal knowledge

---

# Section 8 — Site Documentation Checklist

## 8.1 Minimum Documentation
- [ ] Site label recorded
- [ ] Node ID recorded
- [ ] Date and time recorded
- [ ] Hardware revision recorded
- [ ] Firmware version recorded
- [ ] Deployment tier recorded
- [ ] Installer or team name recorded
- [ ] Power method recorded
- [ ] Communications method recorded
- [ ] Mount type recorded
- [ ] Sensor type recorded
- [ ] Intended sensing target recorded

## 8.2 Site Context Notes
- [ ] Nearby flood behavior or drainage relevance is described
- [ ] Known blockage or trash behavior is described if relevant
- [ ] Backflow suspicion or downstream condition context is described if relevant
- [ ] Any site weakness or uncertainty is documented honestly

## 8.3 Visual Documentation
Where lawful and appropriate:
- [ ] at least one photo or sketch of the installed node is captured
- [ ] at least one view of the sensor target zone is captured
- [ ] at least one close view of the mounting arrangement is captured
- [ ] any sensitive or private details are avoided or redacted as needed

---

# Section 9 — Inspection and Follow-Up Planning

## 9.1 Immediate Follow-Up Plan
- [ ] First inspection date is chosen
- [ ] Responsible person or team is identified
- [ ] Expected service interval is recorded
- [ ] Log retrieval plan is known
- [ ] Fault follow-up plan is known
- [ ] Communications follow-up plan is known

## 9.2 Trigger-Based Follow-Up
The team should define what triggers an early return visit, such as:
- [ ] node silent unexpectedly
- [ ] repeated degraded state
- [ ] enclosure humidity rise
- [ ] persistent alert
- [ ] mounting movement
- [ ] visible debris strike or fouling
- [ ] low battery trend

---

# Section 10 — Deployment Rejection Conditions

A node should **not** be deployed if any of the following are true:

- [ ] the site is not legally accessible
- [ ] the site is unsafe to access
- [ ] the node cannot be serviced later
- [ ] the mount is unstable
- [ ] the sensor has no useful target zone
- [ ] the enclosure sealing is questionable
- [ ] the node has unresolved electrical instability
- [ ] the node cannot log reliably
- [ ] the team cannot document the deployment properly
- [ ] the deployment would create a hazard to the public

Rejecting a bad deployment is a sign of discipline, not failure.

---

# Section 11 — Minimum Deployment Acceptance Rule

A deployment should be considered acceptable only if:

- [ ] the node is ready
- [ ] the site is appropriate
- [ ] the installation is safe
- [ ] the mount is stable
- [ ] the sensing target is valid
- [ ] the node can be serviced later
- [ ] the deployment is documented clearly
- [ ] the team understands the next inspection step

If any of these are missing, the deployment is incomplete.

---

# Section 12 — Post-Deployment Summary Record

After installation, record a short deployment summary with at least:

- node ID
- site label
- deployment date
- deployment status: accepted / needs revision
- main observed strengths
- main observed risks
- next action date
- installer signature or initials if used locally

This summary helps prevent the project from becoming a pile of anonymous hardware.

---

## Summary

This checklist exists to keep **IX-Bayanihan** field deployment disciplined.

A believable flood-support node should not just be built well.

It should also be:

- placed for a real reason
- mounted with care
- documented clearly
- safe to revisit
- honest about its limitations

That is the field standard this repository should uphold.
