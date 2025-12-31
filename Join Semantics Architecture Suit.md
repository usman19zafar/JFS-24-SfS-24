flowchart TD

    A[Enterprise Join Semantics Architecture Suite] --> B[SFS‑24 Structural Layer]
    A --> C[JFS‑24 Operational Layer]

    B --> B1[Preservation contracts<br/>(INNER, LEFT, RIGHT, FULL, CROSS, SELF)]
    B --> B2[NULL‑propagation architecture]
    B --> B3[Structural invariants]
    B --> B4[Collapse boundaries<br/>(outer → inner)]
    B --> B5[24‑cell structural matrix]
    B --> B6[Semantic‑structural 48‑cell matrix]

    C --> C1[Execution‑phase semantics<br/>(ON vs WHERE)]
    C --> C2[Filter‑side safety rules]
    C --> C3[Unsafe collapse patterns<br/>(6 patterns)]
    C --> C4[Join‑filter safety matrix<br/>(24‑cell)]
    C --> C5[Operational doctrine<br/>(WHERE kills NULLs)]
    C --> C6[Governance & linting rules]

    B --- C

    D[Unified Doctrine] --> D1["Joins are preservation contracts"]
    D --> D2["Filters must not violate preservation"]
    D --> D3["Collapse is destruction of the join contract"]

    A --> D
