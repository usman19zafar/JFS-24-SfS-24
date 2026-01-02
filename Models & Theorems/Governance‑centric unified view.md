```mermaid
flowchart TD

A[Unified Join Semantics Governance] --> B[Design Time]
A --> C[Implementation Time]
A --> D[Review & Audit Time]

B --> B1[Declare join preservation intent (SFS-24)]
B --> B2[Choose join type and sides]
B --> B3[Identify preserved vs NULL-producing sides]

C --> C1[Place filters in ON vs WHERE (JFS-24)]
C --> C2[Classify filters (NULL-sensitive vs NULL-neutral)]
C --> C3[Map to 48-cell matrix]

D --> D1[Detect collapse patterns]
D --> D2[Validate against SFS-24 + JFS-24]
D --> D3[Enforce doctrine in code review]
D --> D4[Feed back into training and standards]

E[SFS-24 Assets] --> E1[Preservation model]
E --> E2[NULL-propagation rules]
E --> E3[Structural matrix]

F[JFS-24 Assets] --> F1[Execution-phase model]
F --> F2[Unsafe pattern catalogue]
F --> F3[Safety matrix]

E --> B
F --> C
E --> D
F --> D
...
```
