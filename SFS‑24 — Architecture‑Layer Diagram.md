```mermaid

flowchart TD

    A[**SFS‑24 Structural Framework**] --> B[Layer 1: Preservation Contracts]
    A --> C[Layer 2: NULL Propagation Architecture]
    A --> D[Layer 3: Structural Invariants]
    A --> E[Layer 4: Collapse Conditions]
    A --> F[Layer 5: Semantic Topology (24‑Cell Matrix)]
    A --> G[Layer 6: Structural Doctrine]

    B --> B1[INNER: matched only]
    B --> B2[LEFT: preserve LEFT]
    B --> B3[RIGHT: preserve RIGHT]
    B --> B4[FULL: preserve both]
    B --> B5[CROSS: preserve Cartesian]
    B --> B6[SELF: preserve INNER semantics]

    C --> C1[LEFT JOIN → NULLs on RIGHT]
    C --> C2[RIGHT JOIN → NULLs on LEFT]
    C --> C3[FULL JOIN → NULLs on both]

    D --> D1[Preservation as invariant]
    D --> D2[NULL survival on preserved side]
    D --> D3[Join semantics must remain stable]

    E --> E1[LEFT → INNER collapse]
    E --> E2[RIGHT → INNER collapse]
    E --> E3[FULL → LEFT/RIGHT/INNER collapse]
    E --> E4[CROSS → invalid if ON introduced]

    F --> F1[24‑Cell Structural Matrix]
    F --> F2[48‑Cell Semantic‑Structural Matrix]

    G --> G1["A join is a contract"]
    G --> G2["NULLs are structural signals"]
    G --> G3["Collapse is a semantic failure mode"]
```
