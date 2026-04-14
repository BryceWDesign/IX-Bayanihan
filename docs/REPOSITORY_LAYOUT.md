# IX-Bayanihan Repository Layout

## Purpose

This document defines the intended repository structure for **IX-Bayanihan**.

The goal is to make the project understandable, buildable, and maintainable without relying on hidden assumptions or scattered file placement.

A flood-resilience repository becomes difficult to trust when:

- hardware files are mixed with vague notes
- software files have no clear module boundary
- deployment guidance is disconnected from BOMs
- test artifacts are impossible to trace
- field procedures are buried inside unrelated folders

This layout is designed to prevent that.

---

## Repository Design Philosophy

IX-Bayanihan should be structured so that a serious reader can answer these questions quickly:

- What is this repository for?
- What are the major system layers?
- Where is the proof of concept?
- Where are the BOMs?
- Where are the assembly steps?
- Where are the node definitions?
- Where are the wiring diagrams?
- Where are the test procedures?
- Where are the operations and maintenance files?
- Which files are conceptual and which are build-facing?

The layout must support that kind of fast orientation.

---

## Root Structure Overview

The repository should be organized around the following top-level areas:

- `docs/`
- `bom/`
- `hardware/`
- `firmware/`
- `software/`
- `schemas/`
- `sim/`
- `field/`
- `tests/`
- `assets/`
- `licenses/`

This structure keeps the repository disciplined while leaving room for growth.

---

## Recommended Root Layout

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

This root structure is small enough to stay readable and large enough to support a serious project.

Top-Level Directory Definitions
docs/

This directory holds high-level project documents that explain what the repository is, what it is trying to do, and what its boundaries are.

Typical contents include:

project scope
claim boundary
system architecture
BOM tier strategy
proof-of-concept planning
module specifications
safety notes
design doctrine
deployment philosophy
maintenance philosophy
docs/ exists to answer:
what this project is
how it is supposed to work
what it does not claim
how the pieces fit together
docs/ should not contain:
raw source code
final wiring diagrams
build outputs
unrelated brainstorming fragments

The purpose of docs/ is clarity, not clutter.

bom/

This directory holds bill-of-materials files tied to real builds and real deployment tiers.

It should eventually contain:

proof-of-concept BOMs
hardened-node BOMs
gateway BOMs
node-class-specific BOMs
tier comparison tables
alternative part notes
criticality tagging
bom/ exists to answer:
what parts are needed
which parts are required versus optional
which parts fit which deployment tier
what builders can substitute safely
Example future structure

bom/
├── poc/
├── tier2_field_pilot/
├── tier3_hardened/
├── tier4_reference/
└── shared_parts/

Each BOM file should align directly with a build, not float as an abstract shopping list.

hardware/

This directory holds mechanical, enclosure, mounting, and physical interface documentation for the field nodes.

It should eventually contain:

enclosure layouts
mounting notes
sensor placement notes
splash guards
intake collars
brackets
service access notes
printed part references
housing diagrams
protective shield notes
hardware/ exists to answer:
how the node is physically built
how it is mounted
how it is protected
how it is opened and serviced

Recommended hardware structure

hardware/
├── smart_inlet_node/
├── sentinel_node/
├── gateway_node/
├── shared_mounts/
└── enclosure_notes/

The hardware directory should prefer field-serviceable designs over decorative complexity.

firmware/

This directory holds microcontroller-side logic for the field nodes.

It should eventually contain:

sensor read loops
state machines
threshold handling
degraded-mode logic
alert output logic
local logging
watchdog behavior
communications handling
node self-test behavior
firmware/ exists to answer:
how the field node behaves
how it transitions between states
how it logs events
how it reacts to faults and degraded inputs
Recommended firmware structure

firmware/
├── common/
├── smart_inlet_node/
├── sentinel_node/
├── gateway_helpers/
└── test_harness/

Shared logic should be kept in firmware/common/ rather than duplicated across node folders.

software/

This directory holds operator-facing tools and supporting software beyond microcontroller firmware.

It should eventually contain:

local flood operations console
event viewer
maintenance status view
node registry tools
replay or inspection utilities
log parsers
lightweight dashboards
local dev configuration
software/ exists to answer:
how human operators interpret node behavior
how event data becomes usable
how multiple nodes are summarized
Recommended software structure

software/
├── ops_console/
├── log_tools/
├── maintenance_view/
├── mock_data/
└── shared/

The software layer should stay simple, visible, and reproducible.

schemas/

This directory holds structured definitions for the data used across the repository.

It should eventually contain:

node status schema
event log schema
fault code schema
maintenance record schema
deployment record schema
configuration schema
schemas/ exists to answer:
what fields are expected
what names are stable
what data other modules can rely on

This reduces confusion and prevents every module from inventing its own naming system.

Recommended schema structure

schemas/
├── node_status/
├── event_logs/
├── faults/
├── maintenance/
└── deployment/

The schema layer is critical for discipline and long-term interoperability.

sim/

This directory holds simulation-facing and scenario-testing materials.

It should eventually contain:

threshold simulation inputs
mock flood-event traces
sample event sequences
state transition test inputs
synthetic datasets for console testing
simple evaluation utilities
sim/ exists to answer:
how the design behaves before risky field deployment
how software can be tested without waiting for storms
how state logic can be verified under repeatable inputs
Recommended simulation structure

sim/
├── scenarios/
├── mock_events/
├── threshold_profiles/
└── replay_data/

Simulation is not a replacement for field tests, but it is an important risk reducer.

field/

This directory holds deployment-facing material used by builders and technicians in real or pilot installations.

It should eventually contain:

field deployment checklists
installation notes
inspection forms
service procedures
maintenance intervals
site notes
labeling conventions
safety reminders
example field logs
field/ exists to answer:
how to deploy the node
how to inspect it
how to clean it
how to document what happened in the field
Recommended field structure

field/
├── checklists/
├── deployment_guides/
├── maintenance/
├── service_logs/
└── site_templates/

If the hardware is real but the field pathway is vague, the project will not be trusted.

tests/

This directory holds structured validation artifacts.

It should eventually contain:

bench test checklists
controlled water test procedures
sensor sanity checks
firmware test cases
log verification tests
console behavior checks
regression notes
known-issue reproductions
tests/ exists to answer:
how builders verify the design
what conditions have been tested
whether a change broke something important
Recommended test structure

tests/
├── bench/
├── wet_tests/
├── firmware/
├── console/
└── regression/

A believable project must make testing visible.

assets/

This directory holds supportive visual or non-source materials.

It should eventually contain:

diagrams
icons
printed labels
photos for assembly reference
state indicator legends
service label graphics
example layout figures
assets/ exists to answer:
what the builder should see
what the operator should recognize
how labels and diagrams are shared consistently

This directory should not become a dumping ground for random media.

licenses/

This directory holds supplementary licensing notices if needed.

Because IX-Bayanihan is AGPL-3.0 at the repository level, this directory is useful for:

third-party notices
attribution notes
dependency notices
special file-level clarification if later needed
licenses/ exists to answer:
what outside materials are included
how those materials are licensed
whether any exceptions or notices apply

This directory supports clarity and long-term hygiene.

Recommended Internal Structure by Build

IX-Bayanihan should organize its build-facing artifacts by module class and deployment maturity.

A strong structure keeps the project readable as it grows.

Example build-oriented layout
bom/
├── poc/
│   ├── smart_inlet_node_bom.md
│   ├── sentinel_node_bom.md
│   └── local_console_requirements.md
├── tier2_field_pilot/
├── tier3_hardened/
└── shared_parts/

hardware/
├── smart_inlet_node/
│   ├── enclosure_layout.md
│   ├── mounting_notes.md
│   ├── sensor_placement.md
│   └── service_access.md
├── sentinel_node/
│   ├── enclosure_layout.md
│   ├── mounting_notes.md
│   ├── splash_protection.md
│   └── service_access.md
└── shared_mounts/

firmware/
├── common/
│   ├── states.md
│   ├── fault_codes.md
│   └── signal_conventions.md
├── smart_inlet_node/
│   ├── firmware_spec.md
│   └── thresholds.md
└── sentinel_node/
    ├── firmware_spec.md
    └── thresholds.md

software/
├── ops_console/
│   ├── console_spec.md
│   ├── mock_views.md
│   └── data_ingest.md
└── log_tools/

This pattern supports growth without losing structure.

Documentation Placement Rules

The repository should follow clear placement rules so contributors do not scatter important information.

Rule 1 — Concepts go in docs/

If a file explains the system, its boundary, or its philosophy, it belongs in docs/.

Rule 2 — Parts go in bom/

If a file helps someone procure or compare components, it belongs in bom/.

Rule 3 — Physical build guidance goes in hardware/

If a file explains how a module is shaped, mounted, sealed, or physically assembled, it belongs in hardware/.

Rule 4 — Controller behavior goes in firmware/

If a file explains node logic or embedded behavior, it belongs in firmware/.

Rule 5 — Human-facing software goes in software/

If a file supports operator interpretation, aggregation, or tooling, it belongs in software/.

Rule 6 — Data contracts go in schemas/

If a file defines fields, record structure, state schema, or log formats, it belongs in schemas/.

Rule 7 — Test and validation material goes in tests/ or sim/

If a file exists to verify or replay behavior, it belongs in testing or simulation.

Rule 8 — Field-use procedures go in field/

If a file is meant to be used during deployment, inspection, service, or field review, it belongs in field/.

These rules should remain stable.

File Naming Standards

To keep the repository readable, IX-Bayanihan should follow consistent file naming.

Recommended file naming style

Use lowercase file names with underscores:

smart_inlet_node_bom.md
sentinel_node_assembly.md
event_log_schema.json
field_inspection_checklist.md

This avoids mixed naming styles and improves predictability.

Avoid file names like:
NewDocFinal2.md
final_FINAL_bom.md
random_notes.txt
use_this_one_latest.md

Version confusion destroys trust quickly.

Module Naming Standards

The repository should use a stable set of module names.

Preferred names include:

Smart Inlet Node
Channel / Outfall Sentinel Node
Local Flood Operations Console
Gateway Node
Beacon Node
Relay Node

These names should be reused consistently across:

BOMs
assembly guides
specs
tests
logs
schemas

Do not rename the same concept in every folder.

Versioning and Revision Notes

Every build-facing file should be version-aware.

At minimum, relevant files should indicate:

hardware revision
firmware revision
document revision
date updated
whether the file is proof of concept, pilot, or hardened reference

This makes it easier to compare improvements over time.

Required Document Pairing Rules

Some files should never exist alone.

A BOM should be paired with:
assembly guidance
wiring guidance
maintenance notes
known limitations
A firmware specification should be paired with:
state definitions
input definitions
fault behavior
test notes
A deployment guide should be paired with:
safety notes
checklist
site documentation template
A node specification should be paired with:
BOM
assembly file
maintenance file
test checklist

This pairing rule keeps the repository buildable.

Growth Strategy for the Repository

IX-Bayanihan should grow in a deliberate order.

Early Growth

The first stage should prioritize:

architecture clarity
BOM structure
proof-of-concept definitions
module boundaries
assembly paths
test checklists
Middle Growth

The second stage should add:

node-specific BOMs
assembly instructions
schemas
firmware specifications
operations console specification
field deployment guidance
Mature Growth

The later stage should add:

hardened variants
district integration examples
simulated event traces
structured maintenance workflows
revision history discipline

The repository should not try to look bigger than it is.

Why This Layout Matters for Believability

A serious humanitarian engineering repository must be readable under pressure.

Builders, reviewers, NGOs, municipalities, and researchers should be able to see that:

the project has boundaries
the system has modules
the modules have build paths
the build paths have tests
the tests have outputs
the outputs can be interpreted

That requires structure.

A good layout does not replace good engineering, but a bad layout can make good engineering invisible.

What This Layout Does Not Do

This layout does not guarantee:

perfect implementation
final design quality
regulatory approval
long-term maintainability by itself
field safety by itself

It is not a substitute for the actual work.

It is the scaffolding that lets the actual work stay coherent.

Initial Priority Files to Populate

The most important early files to populate after this layout are:

proof-of-concept BOM for Smart Inlet Node
proof-of-concept BOM for Sentinel Node
Smart Inlet Node assembly walkthrough
Sentinel Node assembly walkthrough
event log schema
node status schema
field deployment checklist
operations console specification
proof-of-concept test checklist
maintenance inspection checklist

These files create the minimum believable build path.

Repository Summary Statement

IX-Bayanihan should be structured so that another motivated builder can move from:

understanding the project
to sourcing parts
to assembling hardware
to configuring software
to testing behavior
to deploying a pilot
to inspecting results

without needing hidden tribal knowledge.

That is the standard this repository layout is meant to support.
