# IX-Bayanihan Smart Inlet Node Assembly Walkthrough

## Purpose

This document provides a full assembly walkthrough for the **IX-Bayanihan Smart Inlet Node proof of concept**.

The goal is to let a careful builder assemble a credible field-capable Smart Inlet Node without relying on hidden assumptions.

This walkthrough is written for a practical proof-of-concept build that can support:

- water-rise detection near a drain or inlet
- threshold state changes
- local visible status
- local event logging
- basic telemetry
- power-state awareness
- degraded-mode behavior
- maintenance-needed signaling

This is not a decorative build.
It is meant to become a real field pilot after bench validation and safe controlled testing.

---

## Scope Boundary

This walkthrough covers assembly of **one Smart Inlet Node** intended for proof-of-concept and field-pilot use.

It does **not** cover:

- municipal mains wiring
- permanent civil installation
- stamped electrical design
- certified lightning protection design
- certified public safety warning deployment
- major floodgate or pump control authority

This is an open field-buildable flood-support node assembly guide.

---

## Recommended Build Profile

This walkthrough assumes a build roughly aligned to the Smart Inlet Node proof-of-concept BOM.

Recommended baseline build:

- ESP32-class controller
- microSD logging
- RTC timekeeping
- primary non-contact water-level sensor
- secondary threshold sensor
- local LED state indicator
- LoRa-capable telemetry path or equivalent
- LiFePO4 battery-backed low-voltage power
- outdoor-capable enclosure with cable glands
- external bracket or protected side mount

If your build deviates, record the differences clearly.

---

## Before You Start

Before assembly begins, confirm the following:

- you have the current Smart Inlet Node BOM
- you know your hardware revision label
- you have chosen your controller and sensor set
- your enclosure is physically large enough for cable bend radius and service access
- your battery and charge path are chemically compatible
- your sensor mounting concept matches the real site type you plan to test

Do not start cutting the enclosure before laying out the internal geometry.

---

## Build Philosophy

The Smart Inlet Node should be assembled with five priorities in this order:

1. electrical safety and stability
2. serviceability
3. enclosure integrity
4. sensor usefulness
5. outward neatness

A clean-looking build that is hard to service or easy to flood internally is a bad build.

---

## Tools and Shop Materials

Typical tools and materials for this build may include:

- small screwdrivers
- wire strippers
- ferrule crimper if using ferrules
- soldering iron if your chosen modules require soldered connections
- heat-shrink tubing
- multimeter
- enclosure drill bits or step bit
- deburring tool
- small hex keys
- label printer or weather-resistant labels
- measuring tape or calipers
- marker for layout
- nylon standoffs or insulated hardware
- zip ties or cable anchors
- threadlocker only where appropriate and service-safe
- clean cloth for final inspection

Do not improvise enclosure penetrations carelessly.

---

## Assembly Overview

The assembly is broken into ten stages:

1. plan the layout
2. pre-fit the enclosure
3. build the power subsystem
4. build the controller and storage subsystem
5. build the sensing subsystem
6. build the local status subsystem
7. install communications hardware
8. complete enclosure and cable routing
9. perform pre-power checks
10. perform first power-on and dry validation

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

Write these down immediately.

Recommended example fields:

- node ID: `inlet-node-001`
- hardware revision: `rev-a`
- deployment tier: `tier2_field_pilot`

This will matter later when logs and labels are generated.

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
- service connectors

Keep these zones conceptually separate even if the enclosure is small.

## 1.3 Draft a Physical Placement Sketch

Before drilling anything, sketch:

- enclosure orientation
- gland positions
- internal board positions
- battery position
- sensor cable entry
- LED indicator position
- antenna route if applicable
- service opening clearance

Make sure the lid can still close without pinching wires.

---

# Stage 2 — Pre-Fit the Enclosure

## 2.1 Choose the Enclosure Orientation

Choose a top, bottom, and service side.

Prefer an orientation where:

- cable entries face downward or sideways, not straight up
- service access is possible without ripping out the battery
- indicator visibility remains practical
- water is less likely to sit around cable penetrations

## 2.2 Mark Penetration Points

Mark the positions for:

- primary sensor cable gland
- secondary sensor cable gland
- power / solar cable gland if external
- antenna gland or bulkhead if needed
- optional LED window or beacon mount
- optional service connector opening if protected

Space penetrations generously enough to avoid crowding.

## 2.3 Drill and Deburr

Cut the required openings carefully.

After drilling:

- deburr every edge
- clean out all plastic or metal chips
- test-fit every gland before mounting electronics
- confirm gasket surfaces remain clean and flat

Loose drill debris inside a flood node is careless and will cause problems later.

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

---

# Stage 3 — Build the Power Subsystem

The power subsystem should be built first because unstable power creates fake problems everywhere else.

## 3.1 Install the Fuse Path

Place the fuse as close as practical to the battery positive feed or primary power input.

The goal is simple:
if something shorts downstream, the fuse should protect the rest of the node.

Do not leave the fuse out “for now.”
Install it as part of the real build.

## 3.2 Install Reverse-Polarity Protection

Add the planned reverse-polarity protection path after the fused input.

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

Do not trust generic board silkscreen blindly.
Verify with documentation and meter checks.

## 3.4 Install the Battery

Mount the battery so that it is:

- secure against vibration
- not crushing wires
- not directly against sharp hardware
- removable for service
- not sitting beneath the most leak-prone point in the enclosure

Use controlled restraint.
Do not let the battery float loose inside the box.

## 3.5 Install the DC Regulation Path

Mount the buck converter or regulated power board.

Then plan and label these rails clearly:

- controller supply rail
- sensor rail if separate
- indicator rail if separate

Keep grounds disciplined.
Star or clean common grounding is better than random daisy-chaining.

## 3.6 Install Voltage / Power Monitoring

Wire the power monitor or sensing divider so the controller can observe supply condition.

At minimum, the node should be able to distinguish:

- healthy supply
- low battery
- unstable power
- return from unstable power

This is part of the node’s truthfulness.

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

- no conductive contact with the enclosure body unless intentionally isolated
- visible access to programming port if needed
- enough clearance for wiring and service
- stable mounting against vibration

## 4.2 Install the microSD Module

Mount the logging module so that:

- the card can be inserted securely
- the card cannot shake loose
- the wiring is short and tidy
- card removal, if needed, is possible without full disassembly

If the SD card is meant to remain installed permanently, make that explicit in the service notes.

## 4.3 Install the RTC Module

Mount the RTC near the controller, keeping wiring neat and documented.

If your design uses network time later, still keep RTC support if possible.
Flood nodes should not lose their timeline the moment communications fail.

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
- power rail note
- battery chemistry
- fuse rating
- date assembled

This matters later when someone other than you opens the node.

---

# Stage 5 — Build the Sensing Subsystem

## 5.1 Install the Primary Water-Level Sensor

For the proof-of-concept Smart Inlet Node, the preferred path is a non-contact sensor.

Mount it so that it can observe a useful target zone while avoiding:

- constant direct trash strike
- pointless sky view
- blind spots caused by bracket geometry
- positions impossible to clean or inspect

The sensor should be mounted using a bracket or hood that protects it without ruining its line of sight.

## 5.2 Install the Sensor Hood or Splash Shield

Add the splash guard or hood around the primary sensor.

Goals:

- reduce direct splash
- reduce accidental impact
- reduce fouling pressure
- preserve measurable line of sight

Do not bury the sensor inside a geometry that makes it impossible to measure anything useful.

## 5.3 Install the Secondary Threshold Sensor

Mount the secondary threshold sensor so that it acts as a simpler confirmation path.

Examples of good roles:
- confirm water has physically reached a known level
- confirm persistent wet state
- backstop ambiguous primary readings

The secondary sensor should not be placed where it is triggered constantly by trivial splash unless that is intended and documented.

## 5.4 Route Sensor Wiring

Run sensor cables through their glands and into the enclosure.

Requirements:

- gentle bend radius
- no sharp chafing points
- no tension on sensor solder joints or terminals
- enough slack for service without leaving large loose loops

Tighten glands only after cable position is finalized.

## 5.5 Install Enclosure Health Sensing

Mount the enclosure humidity / temperature sensor where it measures internal enclosure condition rather than direct external splash.

Do not place it pressed against a heat-generating regulator if you want useful readings.

---

# Stage 6 — Build the Local Status Subsystem

## 6.1 Install the LED or Beacon Indicator

Mount the visible indicator where it can be seen during inspection but is still protected.

Options include:
- sealed LED through panel
- compact beacon on protected face
- internal LED behind a clear window if the window remains readable outdoors

The status indicator must be:
- visible
- serviceable
- understandable

## 6.2 Optional Audio Alert

If using a buzzer:

- place it where it is not directly exposed to water ingress
- ensure it does not compromise enclosure sealing
- treat it as optional, not mandatory

For many deployments, visible status is more appropriate than audible output.

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
- separation from noisy power components if practical
- access for troubleshooting
- mechanical security

## 7.2 Install the Antenna

Install the antenna according to its mounting type.

If external:
- seal the penetration correctly
- avoid strain on the bulkhead or connector
- avoid routing where it will be crushed

If internal:
- keep distance from metal obstructions where possible
- document that performance may be reduced compared with external placement

## 7.3 Preserve a Log-First Philosophy

Even during assembly, remember the intended system behavior:

the node should remain useful when communications fail.

Do not wire the node as if uplink is its only reason for existing.

---

# Stage 8 — Complete Enclosure and Cable Routing

## 8.1 Final Cable Discipline

Before closing the box:

- bundle wires cleanly
- separate power and low-level sensor runs where practical
- prevent wires from pressing hard against enclosure lid edges
- prevent wires from touching hot regulator components
- confirm no wire is trapped under mounting hardware

## 8.2 Tighten Cable Glands

After final routing:

- tighten each gland correctly
- confirm the cable jacket, not the stripped conductor section, is what the gland grips
- do not overtighten to the point of cable damage

## 8.3 Seal Integrity Check

Inspect:
- enclosure gasket
- gland seating
- window or beacon seals
- lid screw seating surfaces

Clean the gasket path before final closure.

## 8.4 Apply External Labels

At minimum apply:

- node ID
- module class
- hardware revision
- service warning or safe-open note if needed

Make it readable by someone in the field.

---

# Stage 9 — Pre-Power Checks

Do not skip this stage.

## 9.1 Electrical Checks

With a meter and visual inspection, confirm:

- battery polarity correct
- regulator output correct
- no short between supply rails
- fuse present
- controller supply within expected range
- no sensor lead swapped in a way that threatens the controller
- antenna connected if required by radio design
- storage card inserted correctly

## 9.2 Mechanical Checks

Confirm:

- boards secure
- battery secure
- sensor mount secure
- LED / beacon secure
- glands tight
- lid closes cleanly
- no internal loose hardware remains

## 9.3 Documentation Checks

Confirm you have recorded:

- node ID
- hardware revision
- date assembled
- selected sensors
- selected battery
- indicator mapping
- radio type
- any build deviations from the BOM

This should happen now, not after a problem appears.

---

# Stage 10 — First Power-On and Dry Validation

## 10.1 Controlled First Power-On

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

## 10.2 Confirm Baseline State

Under dry normal bench conditions, the node should ideally enter:

- BOOT briefly
- then NORMAL if readings are sane

Confirm:
- local status indicator reflects expected baseline
- logs are being written
- timekeeping is sane
- communications heartbeat is sane if configured
- no fake ALERT appears in dry condition

## 10.3 Confirm Primary Sensor Behavior

At dry baseline, confirm the primary sensor produces plausible values.

You are checking for:
- stable reading
- no nonsense oscillation
- no obvious blind geometry
- no wiring noise causing chaos

## 10.4 Confirm Secondary Sensor Behavior

Confirm the secondary threshold sensor is inactive at dry baseline unless intentionally wet-tested.

If it is stuck active unexpectedly:
- inspect placement
- inspect wiring
- inspect threshold logic assumptions

## 10.5 Confirm Logging

Create at least one known event and confirm it appears in storage.

Examples:
- boot event
- heartbeat
- manual test note
- indicator self-test

A node without verifiable logs is not ready for flood-related field claims.

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
Force one safe non-destructive fault condition, such as disconnecting a noncritical sensor path, and confirm the node does not pretend everything is normal.

---

# Initial Wet-Test Preparation

Before the first controlled wet test:

- confirm the enclosure is closed correctly
- confirm the sensing zone is accessible
- confirm there is a safe way to add and remove water
- confirm mains-powered equipment is not exposed
- confirm you can stop the test instantly if needed
- confirm a dry cloth and inspection tools are available
- confirm logs are retrievable after the test

The wet test should be safe, repeatable, and boring in the best way.

---

# Field-Mount Preparation Notes

Do not mount the Smart Inlet Node at the real site until the following are true:

- the node boots reliably
- the baseline dry state is stable
- the logs work
- the status indicator works
- the sensor mount geometry is understood
- the enclosure can be opened and reclosed without damage
- the builder knows how to inspect and clean the sensor path

A node that only “sort of works” on the bench is not ready for a street drain.

---

# Common Assembly Mistakes to Avoid

## Mistake 1 — Building Around the Enclosure Too Late
If you wire everything before planning enclosure geometry, the result is usually poor.

## Mistake 2 — Treating the Battery as an Afterthought
The battery placement affects serviceability, heat, and enclosure integrity.

## Mistake 3 — Overcrowding Cable Entries
Too many rushed penetrations create ingress risk and maintenance misery.

## Mistake 4 — Prioritizing Pretty Layout Over Service Access
A neat build that cannot be opened cleanly is not a serious flood node.

## Mistake 5 — Mounting the Sensor Where It Cannot Actually Observe Useful Water Change
This kills the node’s entire reason for existing.

## Mistake 6 — Relying on Communications Instead of Local Truth
The node must still be meaningful when radio is weak or absent.

## Mistake 7 — Closing the Enclosure Before a Full Meter Check
That is how preventable electrical mistakes survive into field deployment.

---

# Minimum Assembly Acceptance Criteria

The Smart Inlet Node assembly should be considered acceptable for controlled testing only if all of the following are true:

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
- builder name
- known assembly deviations
- open issues before field testing

Store that record with the node documentation.

---

# Summary

This assembly walkthrough is designed to produce a **credible Smart Inlet Node proof-of-concept build** for IX-Bayanihan.

If assembled carefully, the node should be able to:

- sense local water-rise conditions
- preserve event evidence
- show local state visibly
- survive basic outdoor pilot deployment
- support future maintenance and iteration

That is the correct assembly standard for this stage of the project.
