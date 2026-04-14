# IX-Bayanihan Channel / Outfall Sentinel Node Assembly Walkthrough

## Purpose

This document provides a full assembly walkthrough for the **IX-Bayanihan Channel / Outfall Sentinel Node proof of concept**.

The goal is to let a careful builder assemble a credible exposed-environment flood corridor node without relying on hidden assumptions.

This walkthrough is written for a practical proof-of-concept build that can support:

- broader water-level awareness at channels, esteros, culverts, and outfalls
- trend-based flood condition visibility
- optional backflow-context awareness
- local visible node status
- local event logging
- basic telemetry
- power-state awareness
- degraded-mode behavior
- maintenance-needed signaling

This is not a decorative build.
It is meant to become a real exposed field pilot after bench validation and safe controlled testing.

---

## Scope Boundary

This walkthrough covers assembly of **one Channel / Outfall Sentinel Node** intended for proof-of-concept and field-pilot use.

It does **not** cover:

- major municipal pump control
- floodgate actuation packages
- permanent structural marine works
- stamped structural design
- certified lightning or surge protection packages for critical infrastructure
- legal public warning authority
- autonomous command over public flood-control systems

This is an open field-buildable flood-support node assembly guide for exposed monitoring locations.

---

## Recommended Build Profile

This walkthrough assumes a build roughly aligned to the Sentinel Node proof-of-concept BOM.

Recommended baseline build:

- ESP32-class controller
- microSD logging
- RTC timekeeping
- primary outdoor-capable non-contact level sensor
- secondary threshold sensor
- local LED or compact beacon state indicator
- LoRa-capable telemetry path or equivalent
- LiFePO4 battery-backed low-voltage power
- outdoor-capable UV-stable enclosure with cable glands
- rigid external bracket or protected side mount
- sensor hood or splash guard

If your build deviates, record the differences clearly.

---

## Before You Start

Before assembly begins, confirm the following:

- you have the current Sentinel Node BOM
- you know your hardware revision label
- you have chosen your controller and sensor set
- your enclosure is large enough for service access and cable bend radius
- your battery and charge path are chemically compatible
- your planned sensor mounting geometry actually matches the water corridor you want to observe
- your selected mounting location concept is serviceable and safe

Do not start drilling the enclosure before laying out the internal geometry and external sensor orientation.

---

## Build Philosophy

The Channel / Outfall Sentinel Node should be assembled with five priorities in this order:

1. electrical safety and stability
2. enclosure survivability
3. serviceability
4. sensor usefulness and alignment
5. outward neatness

A clean-looking exposed node that leaks, drifts, or cannot be re-aimed is a bad build.

---

## Tools and Shop Materials

Typical tools and materials for this build may include:

- small screwdrivers
- wire strippers
- ferrule crimper if using ferrules
- soldering iron if required by your modules
- heat-shrink tubing
- multimeter
- enclosure drill bits or step bit
- deburring tool
- small hex keys
- weather-resistant labels
- measuring tape or calipers
- marker for layout
- nylon standoffs or insulated mounting hardware
- zip ties or cable anchors
- threadlocker only where appropriate and service-safe
- clean cloth for final inspection
- bracket-alignment tools appropriate to your chosen mount

Because this node is meant for exposed locations, do not improvise sloppy penetrations or weak external brackets.

---

## Assembly Overview

The assembly is broken into eleven stages:

1. plan the layout
2. pre-fit the enclosure
3. build the power subsystem
4. build the controller and storage subsystem
5. build the sensing subsystem
6. build the local status subsystem
7. install communications hardware
8. build the external mounting and sensor aim hardware
9. complete enclosure and cable routing
10. perform pre-power checks
11. perform first power-on and dry validation

Follow the order.  
Do not jump directly to final closure.

---

# Stage 1 — Plan the Layout

## 1.1 Assign a Node Identity

Before touching the enclosure, assign:

- node ID
- site label placeholder
- hardware revision
- intended deployment tier
- intended sensor arrangement
- intended mounting type

Write these down immediately.

Recommended example fields:

- node ID: `sentinel-node-001`
- hardware revision: `rev-a`
- deployment tier: `tier2_field_pilot`
- mount type: `wall_bracket_side_view`

This matters later when labels, logs, and maintenance notes are generated.

## 1.2 Separate the Build into Zones

Divide the enclosure internally into these logical zones:

### Power Zone
For:
- battery input
- charge controller
- fuse
- reverse-polarity protection
- buck converter
- power monitor

### Logic Zone
For:
- controller board
- SD storage
- RTC
- optional local connectors

### Sensor / I/O Zone
For:
- primary sensor wiring
- secondary threshold input
- LED or beacon output
- communications routing
- optional camera or future viewport support
- service connectors

Keep these zones conceptually separate even if the enclosure is compact.

## 1.3 Draft a Physical Placement Sketch

Before drilling anything, sketch:

- enclosure orientation
- gland positions
- internal board positions
- battery position
- sensor cable entry
- LED / beacon position
- antenna route if applicable
- service opening clearance
- external sensor bracket direction
- sensor sightline toward the intended water surface

Make sure the lid can still close without pinching wires and that the sensor sightline remains useful.

---

# Stage 2 — Pre-Fit the Enclosure

## 2.1 Choose the Enclosure Orientation

Choose a top, bottom, and service side.

Prefer an orientation where:

- cable entries face downward or sideways, not straight up
- service access is possible without removing the whole mount
- indicator visibility remains practical
- water is less likely to pool around cable penetrations
- the sensor cable run does not force awkward bends

## 2.2 Mark Penetration Points

Mark the positions for:

- primary sensor cable gland
- secondary sensor cable gland
- power / solar cable gland if external
- antenna gland or bulkhead if needed
- optional beacon mount
- optional camera window if ever used
- optional service connector opening if protected

Space penetrations generously enough to avoid crowding.

## 2.3 Drill and Deburr

Cut the required openings carefully.

After drilling:

- deburr every edge
- clean out all chips
- test-fit every gland before mounting electronics
- confirm gasket surfaces remain clean and flat
- ensure no sharp cut edge threatens cable jackets

Loose debris inside an exposed flood node is a preventable error.

## 2.4 Dry-Fit the Internal Components

Without wiring yet, place:

- battery
- controller
- storage module
- RTC
- charge controller
- buck converter
- fuse holder
- power monitor
- terminal blocks
- cable routes

Check that:
- no board touches the lid
- no wire run must fold sharply
- the battery can be replaced later
- the SD card remains accessible if local removal is part of your plan
- the enclosure can still close cleanly
- sensor and antenna penetrations make routing sense

---

# Stage 3 — Build the Power Subsystem

The power subsystem should be built first because unstable power creates fake sensor and communications problems.

## 3.1 Install the Fuse Path

Place the fuse as close as practical to the battery positive feed or primary power input.

The goal is simple:
if something shorts downstream, the fuse should protect the rest of the node.

Do not omit the fuse.

## 3.2 Install Reverse-Polarity Protection

Add the reverse-polarity protection path after the fused input.

This may be:
- diode-based
- MOSFET-based
- part of a protected input board

Record which approach you used.

## 3.3 Install the Charge Controller

If using solar and LiFePO4:

- mount the charge controller securely
- confirm battery chemistry compatibility
- confirm solar input polarity
- confirm battery output polarity
- label all terminals clearly

Do not trust generic board markings blindly.
Verify with documentation and meter checks.

## 3.4 Install the Battery

Mount the battery so that it is:

- secure against vibration
- not crushing wires
- not touching sharp hardware
- removable for service
- not directly below the most likely ingress point

Use controlled restraint.
Do not let the battery move inside the enclosure.

## 3.5 Install the DC Regulation Path

Mount the buck converter or regulated power board.

Then plan and label these rails clearly:

- controller supply rail
- sensor rail if separate
- indicator rail if separate
- optional camera or radio accessory rail if used

Keep grounding disciplined.
A clean common reference is better than random daisy-chaining.

## 3.6 Install Voltage / Power Monitoring

Wire the power monitor or sensing divider so the controller can observe supply condition.

At minimum, the node should be able to distinguish:

- healthy supply
- low battery
- unstable power
- return from unstable power

This is part of the node’s truthfulness in the console and logs.

## 3.7 Perform an Unloaded Power Check

Before connecting the controller or sensors:

- confirm battery voltage at source
- confirm regulated output voltage
- confirm no reverse polarity downstream
- confirm no abnormal heating
- confirm fuse continuity
- confirm charge-controller output behavior

Do not continue if these checks are not clean.

---

# Stage 4 — Build the Controller and Storage Subsystem

## 4.1 Mount the Controller Board

Install the controller on standoffs or a mounting plate.

Requirements:

- no conductive contact with enclosure body unless intentionally isolated
- visible access to programming port if needed
- enough clearance for wiring and service
- stable mounting against vibration

## 4.2 Install the microSD Module

Mount the logging module so that:

- the card can be inserted securely
- the card cannot shake loose
- wiring remains short and tidy
- card removal, if needed, is possible without destroying the layout

If the SD card is meant to remain installed permanently, record that in service notes.

## 4.3 Install the RTC Module

Mount the RTC near the controller, keeping wiring neat and documented.

Flood corridor nodes often face intermittent connectivity.
Keep timekeeping local when possible.

## 4.4 Wire Controller, Storage, and RTC

Complete the low-voltage signal wiring carefully.

Good practice:

- use color discipline
- label conductors where practical
- secure wires away from lid pinch points
- avoid bare exposed joints
- support wires mechanically before final closure

## 4.5 Add a Service Label Inside the Enclosure

At minimum, include:

- node ID
- hardware revision
- battery chemistry
- fuse rating
- date assembled
- regulator output value

This matters later when someone else opens the node.

---

# Stage 5 — Build the Sensing Subsystem

## 5.1 Install the Primary Water-Level Sensor

For the Sentinel Node, the preferred path is an outdoor-capable non-contact sensor.

Mount it so that it can observe a useful water-surface region while avoiding:

- pointless sky view
- blind bracket geometry
- permanent obstruction by railings or walls
- direct continuous heavy trash strike
- impossible cleaning access

The sensor should be mounted with enough stability that its aim does not drift easily.

## 5.2 Install the Sensor Hood or Splash Shield

Add the splash guard or hood around the primary sensor.

Goals:

- reduce direct splash
- reduce debris strike
- reduce solar glare or contamination pressure where relevant
- preserve measurable line of sight

Do not bury the sensor in a shield geometry that ruins measurement.

## 5.3 Install the Secondary Threshold Sensor

Mount the secondary threshold sensor so that it acts as a simpler confirmation path.

Examples of good roles:
- confirm water reached a known elevation
- confirm persistent high-water state
- backstop ambiguous primary readings

The secondary sensor should not be placed where it is triggered constantly by trivial splash unless that is deliberate and documented.

## 5.4 Route Sensor Wiring

Run sensor cables through their glands and into the enclosure.

Requirements:

- gentle bend radius
- no chafing points
- no tension on terminals or solder joints
- enough slack for service without leaving large loose loops

Tighten glands only after final cable position is set.

## 5.5 Install Enclosure Health Sensing

Mount the enclosure humidity / temperature sensor where it measures internal enclosure condition rather than direct external splash or regulator heat.

It should help indicate:
- enclosure stress
- moisture ingress risk
- overheating trends

---

# Stage 6 — Build the Local Status Subsystem

## 6.1 Install the LED or Beacon Indicator

Mount the visible indicator where it can be seen during inspection but is still protected.

Options include:
- sealed LED through panel
- compact external beacon on protected face
- internal LED behind a clear sealed window

The status indicator must be:
- visible
- serviceable
- understandable in daylight

## 6.2 Optional Audio Alert

If using a buzzer:

- place it where it does not compromise enclosure sealing
- keep it protected from direct water exposure
- treat it as optional, not required

For many corridor deployments, visible status is better than sound.

## 6.3 Confirm State Mapping Documentation

Before final closure, record the intended indicator mapping such as:

- green = NORMAL
- yellow = WATCH
- red = ALERT
- distinct blink = DEGRADED / FAULT / SERVICE

Do not rely on memory.

---

# Stage 7 — Install Communications Hardware

## 7.1 Mount the Radio Module

Mount the communications module with attention to:

- antenna routing
- separation from noisy power components where practical
- access for troubleshooting
- mechanical stability

## 7.2 Install the Antenna

Install the antenna according to its mounting type.

If external:
- seal the penetration correctly
- avoid strain on the connector
- avoid route paths where it can be snagged or crushed

If internal:
- keep as much distance from metal obstructions as practical
- record that performance may be reduced

## 7.3 Preserve a Log-First Philosophy

Even during assembly, keep the intended behavior in mind:

the node should remain useful when communications fail.

Do not build it as if uplink is its only reason to exist.

---

# Stage 8 — Build the External Mounting and Sensor Aim Hardware

This stage matters more for the Sentinel Node than for the street node because bad aiming destroys corridor visibility.

## 8.1 Choose the Mount Type

Use a mount appropriate to the site concept, such as:

- wall bracket
- rail bracket
- pole clamp
- side-mounted backplate
- protected bridge-side bracket

The mount should allow:
- stable sensor aim
- service access
- enclosure removal if needed
- no obstruction of water flow

## 8.2 Install the Enclosure Mount Bracket

Secure the enclosure bracket so that it:

- resists vibration
- does not twist easily
- keeps the enclosure vertical or intentionally angled
- allows safe service access

Avoid weak strap-only arrangements unless the node is for a very temporary dry run.

## 8.3 Install the Sensor Aim Bracket

The sensor aim bracket is critical.

Set it so that:
- the sensor looks at a known water target zone
- the target zone is not hidden by wall edges, bars, or hardware
- the sensor does not point into direct useless reflection geometry
- the sensor remains adjustable for early tuning

Record the initial aim geometry in notes.

## 8.4 Add External Guarding if Needed

If the site concept suggests likely bird fouling, debris strike, or incidental contact, add a simple guard that:

- does not block the sensor view
- does not trap water
- does not make service impossible

---

# Stage 9 — Complete Enclosure and Cable Routing

## 9.1 Final Cable Discipline

Before closing the box:

- bundle wires cleanly
- separate power and low-level sensor runs where practical
- prevent wires from pressing hard against lid edges
- prevent wires from touching hot components
- confirm no wire is trapped under hardware

## 9.2 Tighten Cable Glands

After final routing:

- tighten each gland correctly
- confirm the cable jacket, not bare conductors, is what the gland grips
- do not overtighten to the point of cable damage

## 9.3 Seal Integrity Check

Inspect:
- enclosure gasket
- gland seating
- beacon or LED seals
- antenna bulkhead seal if used
- lid screw seating surfaces

Clean the gasket path before final closure.

## 9.4 Apply External Labels

At minimum apply:

- node ID
- module class
- hardware revision
- service warning or safe-open note if needed

Make it readable by someone in the field.

---

# Stage 10 — Pre-Power Checks

Do not skip this stage.

## 10.1 Electrical Checks

With a meter and visual inspection, confirm:

- battery polarity correct
- regulator output correct
- no short between supply rails
- fuse present
- controller supply within expected range
- no sensor lead swapped in a dangerous way
- antenna connected if required by radio design
- storage card inserted correctly

## 10.2 Mechanical Checks

Confirm:

- boards secure
- battery secure
- sensor mount secure
- beacon / indicator secure
- glands tight
- external mount secure
- sensor aim bracket secure
- lid closes cleanly
- no internal loose hardware remains

## 10.3 Documentation Checks

Confirm you have recorded:

- node ID
- hardware revision
- date assembled
- selected sensors
- selected battery
- indicator mapping
- radio type
- mount type
- initial sensor aim note
- any build deviations from the BOM

This should be done now, not later.

---

# Stage 11 — First Power-On and Dry Validation

## 11.1 Controlled First Power-On

Perform the first power-on in a controlled dry environment.

Observe:

- boot indicator
- controller startup
- abnormal heat
- smoke or smell
- reset looping
- SD initialization behavior
- sensor startup behavior
- visible indicator behavior

If anything looks wrong, stop and inspect before continuing.

## 11.2 Confirm Baseline State

Under dry normal bench conditions, the node should ideally enter:

- BOOT briefly
- then NORMAL if readings are sane

Confirm:
- local indicator reflects expected baseline
- logs are being written
- timekeeping is sane
- communications heartbeat is sane if configured
- no fake ALERT appears in dry condition

## 11.3 Confirm Primary Sensor Behavior

At dry baseline, confirm the primary sensor produces plausible values.

You are checking for:
- stable reading
- no nonsense oscillation
- no blind geometry
- no severe noise from wiring or regulator behavior

## 11.4 Confirm Secondary Sensor Behavior

Confirm the secondary threshold sensor is inactive at dry baseline unless intentionally wet-tested.

If it is stuck active unexpectedly:
- inspect placement
- inspect wiring
- inspect logic assumptions

## 11.5 Confirm Logging

Create at least one known event and confirm it appears in storage.

Examples:
- boot event
- heartbeat
- manual test note
- indicator self-test

A corridor node without verifiable logs is not ready for field claims.

---

# Controlled Functional Check Before Wet Testing

Before moving to water simulation, perform these dry functional checks.

## Dry Functional Check A — Indicator Test
Trigger each state indicator path in a controlled way and verify the visible output.

## Dry Functional Check B — Communications Check
Verify the node can transmit a basic record or heartbeat if communications are enabled.

## Dry Functional Check C — Power Reporting Check
Confirm the controller can observe supply condition and report at least one normal power reading.

## Dry Functional Check D — Fault Path Check
Force one safe non-destructive fault condition, such as disconnecting a noncritical sensing path, and confirm the node does not pretend everything is normal.

## Dry Functional Check E — Aim Stability Check
Touch-test the mount gently and confirm the sensor aim does not shift easily or drift into useless geometry.

---

# Initial Wet-Test Preparation

Before the first controlled wet test:

- confirm the enclosure is closed correctly
- confirm the sensing zone is accessible
- confirm there is a safe way to add and remove water or simulate water level
- confirm mains-powered equipment is not exposed
- confirm you can stop the test instantly if needed
- confirm drying materials and inspection tools are available
- confirm logs are retrievable after the test

The wet test should be safe, repeatable, and boring in the best way.

---

# Field-Mount Preparation Notes

Do not mount the Sentinel Node at a real exposed site until the following are true:

- the node boots reliably
- the dry baseline is stable
- the logs work
- the status indicator works
- the sensor geometry is understood
- the enclosure can be opened and reclosed without damage
- the mount can be serviced safely
- the sensor can be inspected and cleaned without dangerous access

A node that only “mostly works” on the bench is not ready for a channel or outfall edge.

---

# Common Assembly Mistakes to Avoid

## Mistake 1 — Treating the Mount as Secondary
For this node, bad mounting ruins the measurement and the service path.

## Mistake 2 — Aiming the Sensor Without a Defined Target Zone
If you do not know what surface region you are measuring, the readings may become meaningless.

## Mistake 3 — Overcrowding Cable Entries
Crowded penetrations create ingress risk and maintenance misery.

## Mistake 4 — Prioritizing Compactness Over Service Access
If the battery or SD card cannot be reached, later maintenance becomes painful.

## Mistake 5 — Forgetting Exposure Reality
This node must tolerate splash, dirt, vibration, and stronger weather than a bench prototype.

## Mistake 6 — Depending on Communications for Truth
The node must still preserve evidence locally.

## Mistake 7 — Weak External Hardware
A bracket that twists, rusts, or loosens will destroy credibility quickly.

---

# Minimum Assembly Acceptance Criteria

The Sentinel Node assembly should be considered acceptable for controlled testing only if all of the following are true:

- enclosure closes cleanly
- power rails are correct
- controller boots reliably
- primary sensor is readable
- secondary sensor is readable if installed
- local indicator works
- logs can be created and retrieved
- battery path is stable
- fuse is installed
- cable entries are secured
- external mount is secure
- sensor aim is stable
- node identity is labeled
- the builder can explain how to service the unit later

If any of these are missing, the build is not finished.

---

# Post-Assembly Record

After assembly, record at minimum:

- node ID
- hardware revision
- assembly date
- controller type
- primary sensor type
- secondary sensor type
- storage type
- power subsystem type
- communications type
- enclosure type
- mount type
- initial aim notes
- builder name
- known assembly deviations
- open issues before field testing

Store that record with the node documentation.

---

# Summary

This assembly walkthrough is designed to produce a **credible Channel / Outfall Sentinel Node proof-of-concept build** for IX-Bayanihan.

If assembled carefully, the node should be able to:

- sense broader water corridor conditions
- preserve event evidence
- show local state visibly
- survive basic exposed outdoor pilot deployment
- support future maintenance and iteration

That is the correct assembly standard for this stage of the project.
