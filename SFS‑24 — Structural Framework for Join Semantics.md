SFS‑24 — Structural Framework for Join Semantics
24‑Cell Structural Architecture Standard
Version 1.0 — 2025  
Author: Usman Zafar

1. Purpose
SFS‑24 defines the structural semantics of relational joins.
It establishes the preservation guarantees, NULL‑propagation rules, collapse boundaries, and structural invariants that govern join behavior across analytical, operational, and ETL/ELT systems.

This standard ensures that join logic remains:

predictable

reproducible

auditable

structurally correct

SFS‑24 is the structural counterpart to JFS‑24, which governs filter safety.

2. Scope
SFS‑24 applies to:

data warehouses and lakehouses

ETL/ELT pipelines

BI semantic layers

dimensional modeling

fact‑table construction

SQL governance and code review

It covers the structural behavior of:

INNER JOIN

LEFT JOIN

RIGHT JOIN

FULL JOIN

CROSS JOIN

SELF JOIN

3. Structural Principles
3.1 Joins as Preservation Contracts
Each join type defines a contract specifying which rows must be preserved.

Join Type	Preservation Contract
INNER	Preserve matched rows only
LEFT	Preserve all LEFT rows
RIGHT	Preserve all RIGHT rows
FULL	Preserve all rows from both sides
CROSS	Preserve Cartesian product
SELF	Preserve INNER semantics
Architectural Principle:

A join is not an operation. A join is a contract.

3.2 NULL as a Structural Signal
NULLs produced by joins are not values — they are structural indicators representing:

missing relationships

incomplete dimensions

orphaned facts

preservation boundaries

NULL propagation determines:

referential integrity

dimensional completeness

fact‑table grain correctness

outer‑join stability

NULL behavior is a first‑class architectural concern.

3.3 Structural Invariants
SFS‑24 defines the following invariants:

Preservation is mandatory  
A join must preserve the rows defined by its contract.

NULLs must survive on the preserved side  
Eliminating NULL‑extended rows collapses the join.

Join semantics must remain stable  
A LEFT JOIN must remain a LEFT JOIN unless explicitly changed.

Matching and elimination must remain separate phases  
(Matching = ON, Elimination = WHERE)

These invariants form the backbone of SFS‑24.

4. NULL‑Propagation Architecture
4.1 LEFT JOIN
Preserves LEFT rows

Produces NULLs on RIGHT side

4.2 RIGHT JOIN
Preserves RIGHT rows

Produces NULLs on LEFT side

4.3 FULL JOIN
Preserves both sides

Produces NULLs on both sides

4.4 INNER JOIN
Produces no structural NULLs

Eliminates unmatched rows

4.5 CROSS JOIN
Produces no structural NULLs

No matching condition

NULL propagation is the structural signature of each join type.

5. Collapse Conditions (Outer → Inner)
A join collapses when its NULL‑extended rows are eliminated.

5.1 LEFT JOIN Collapse
Occurs when RIGHT‑side NULLs are removed.

5.2 RIGHT JOIN Collapse
Occurs when LEFT‑side NULLs are removed.

5.3 FULL JOIN Collapse
Can collapse into:

LEFT JOIN

RIGHT JOIN

INNER JOIN

depending on which side’s NULLs are eliminated.

5.4 CROSS JOIN Collapse
Occurs when an ON condition is introduced.

Collapse is a semantic failure mode.

6. The 24‑Cell Structural Matrix
SFS‑24 classifies join‑side × filter‑side × phase interactions into:

SAFE

COLLAPSE

INVALID

NEUTRAL

JOIN TYPE	      LEFT     WHERE	LEFT ON	RIGHT WHERE	RIGHT ON
INNER	SAFE	    SAFE	   SAFE	SAFE
LEFT	SAFE	    SAFE	   COLLAPSE	SAFE
RIGHT	COLLAPSE	SAFE	   SAFE	SAFE
FULL	COLLAPSE	SAFE	   COLLAPSE	SAFE
CROSS	SAFE	    INVALID	 SAFE	INVALID
SELF	SAFE	    SAFE	   SAFE	SAFE

This matrix is the structural topology of join semantics.

7. The 48‑Cell Semantic‑Structural Matrix
The full 48‑cell matrix extends the structural matrix by incorporating:

filter type (EQ, NE, GT, IS NULL, IS NOT NULL)

filter placement (ON vs WHERE)

join type

preserved side

NULL‑producing side

This matrix is the authoritative reference for structural correctness.

See:
docs/30-unified-architecture/semantic-structural-48-cell-matrix.md

8. Structural Doctrine
SFS‑24 establishes the following doctrine:

Joins are preservation contracts

NULLs are structural signals

Collapse is a semantic failure mode

ON defines matching

WHERE defines elimination

Preservation must never be violated

This doctrine elevates join reasoning to the level of enterprise architecture.

9. Compliance Requirements
To comply with SFS‑24:

Do not eliminate NULL‑extended rows on the preserved side

Do not introduce ON conditions into CROSS JOINs

Do not rely on implicit join behavior

Validate all joins against the structural matrix

Document preservation intent in design artifacts

10. Relationship to JFS‑24
SFS‑24 defines what the join must preserve.
JFS‑24 defines how filters must behave to preserve it.

Together, they form the Enterprise Join Semantics Architecture Suite.

JFS‑24 Standard:
docs/20-jfs24-filter-safety/jfs24-standard.md

11. Versioning
SFS‑24 follows semantic versioning:

Major — structural changes

Minor — new invariants or matrices

Patch — clarifications or examples

See:
docs/90-legal-and-metadata/versioning-and-changelog.md

12. Copyright
© 2025 Usman Zafar. All rights reserved.
This standard is proprietary intellectual property.
