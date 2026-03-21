# IX-Bayanihan License Stack

Copyright 2026 Bryce Lovell

IX-Bayanihan is structured as a mixed-discipline public-interest engineering
repository. Different asset classes in this repository are intentionally licensed
under different licenses so that software, hardware design material, and
documentation/media are all governed by terms that fit their actual use.

This file defines the license map for the repository.

## 1) License Stack

### A. Software / Source Code
License:
- GNU Affero General Public License v3.0 only
- SPDX identifier: `AGPL-3.0-only`

Applies to:
- application code
- firmware
- embedded software
- scripts
- automation
- simulation code
- analysis code
- testing code
- deployment utilities
- software configuration files where copyright applies

Typical paths:
- `/software/**`
- `/firmware/**`
- `/scripts/**`
- `/tools/**`
- `/sim/**`
- `/tests/**`

Typical file examples:
- `.py`
- `.c`
- `.cpp`
- `.h`
- `.hpp`
- `.rs`
- `.js`
- `.ts`
- `.sh`
- `.ps1`
- `.m`
- executable build/config files primarily intended to run as code

Rationale:
AGPLv3 keeps software freedom intact even when modified versions are used over a
network or delivered as a service. That aligns with the public-benefit goal of
IX-Bayanihan and reduces the risk of silent privatization of deployment-side
software improvements.

---

### B. Hardware / Design Source / Fabrication Material
License:
- CERN Open Hardware Licence Version 2 - Strongly Reciprocal
- SPDX identifier: `CERN-OHL-S-2.0`

Applies to:
- electrical schematics
- PCB layouts
- CAD files
- mechanical drawings
- fabrication drawings
- enclosure geometry
- wiring harness drawings
- manufacturing design files
- system integration drawings
- hardware design source files
- bill of materials files tightly coupled to hardware construction

Typical paths:
- `/hardware/**`
- `/electronics/**`
- `/mechanical/**`
- `/cad/**`
- `/pcb/**`
- `/manufacturing/**`

Typical file examples:
- `.kicad_sch`
- `.kicad_pcb`
- `.step`
- `.stp`
- `.f3d`
- `.FCStd`
- `.dxf`
- `.dwg`
- `.svg` when used as fabrication geometry
- `.csv` or `.xlsx` when used as hardware BOM/design-source support
- manufacturing notes tied directly to hardware replication

Rationale:
CERN-OHL-S v2 is intended for open hardware design source and requires modified
versions and derived design material to remain openly available under the same
strongly reciprocal framework.

---

### C. Documentation / Media / Non-Code Explanatory Content
License:
- Creative Commons Attribution-ShareAlike 4.0 International
- SPDX identifier: `CC-BY-SA-4.0`

Applies to:
- explanatory documentation
- manuals
- white papers
- concept notes
- architecture narratives
- diagrams intended as explanatory figures
- images
- rendered media
- training material
- deployment guides
- public communication material
- non-code specifications written for human reading

Typical paths:
- `/docs/**`
- `/media/**`
- `/images/**`
- `/diagrams/**`
- `/training/**`
- `/field-guides/**`

Typical file examples:
- `.md`
- `.txt`
- `.pdf`
- `.png`
- `.jpg`
- `.jpeg`
- `.webp`
- `.drawio`
- `.pptx` if used as documentation/media
- `.svg` when used as an explanatory diagram rather than fabrication geometry

Rationale:
CC BY-SA 4.0 preserves attribution and share-alike behavior for documentation and
educational material while remaining broadly accessible.

---

## 2) Boundary Rules

Because IX-Bayanihan spans software, hardware, and documentation, some files may
appear ambiguous unless the boundary rules are stated clearly.

### Rule 1: File function controls classification
A file is classified by what it is principally for.

- If it is meant to execute on a machine, it is software.
- If it is design source for something to be fabricated or assembled, it is hardware.
- If it is explanatory material for humans, it is documentation/media.

### Rule 2: Path is persuasive, not absolute
Directory placement is strong evidence of the intended license, but the actual
function of the file controls if there is a conflict.

### Rule 3: Embedded code inside documentation
Short code snippets included only for explanation inside documentation remain part
of the documentation unless they are explicitly marked as runnable project code.

### Rule 4: Buildable design scripts
Scripts whose primary purpose is to generate, parameterize, or manufacture hardware
design outputs may be placed with hardware design material and treated as hardware
design source where appropriate. General-purpose utilities remain software.

### Rule 5: Dual-content files
If a file combines substantial code and substantial documentation, the repository
maintainer may split the file in a later revision or add an explicit file-level
notice to remove ambiguity.

---

## 3) File-Level Notices and SPDX Practice

Where practical, source files should carry SPDX identifiers matching their
assigned license.

Examples:
- `SPDX-License-Identifier: AGPL-3.0-only`
- `SPDX-License-Identifier: CERN-OHL-S-2.0`
- `SPDX-License-Identifier: CC-BY-SA-4.0`

If a file lacks an SPDX header, this license map still governs unless a more
specific file-level notice states otherwise.

---

## 4) Inbound Contributions

Unless explicitly stated otherwise in a future contribution policy, any accepted
contribution is understood to be provided under the license applicable to the
location and function of the contributed material.

Examples:
- code contribution into `/software/` -> AGPL-3.0-only
- PCB update in `/hardware/pcb/` -> CERN-OHL-S-2.0
- deployment guide in `/docs/` -> CC-BY-SA-4.0

Contributors should avoid submitting material that they do not have the right to
license under the applicable terms.

---

## 5) No Trademark Grant

This repository license stack governs copyright and, where applicable, patent or
hardware design rights under the chosen licenses. It does not grant trademark
rights in the project name, branding, logos, or visual identity unless a separate
written statement says otherwise.

---

## 6) Humanitarian Intent

IX-Bayanihan is intended as a public-benefit engineering effort aimed at practical,
field-deployable resilience infrastructure. The selected licenses are meant to keep
the work broadly usable while preserving downstream openness.

That humanitarian intent does not override the actual legal text of the underlying
licenses. The license texts themselves control.

---

## 7) Controlling Text

This file is a repository-level license map only. It does not replace the full text
of the licenses named above. Where this file and a license text differ, the license
text controls.

Future commits add the corresponding full license texts to the repository.
