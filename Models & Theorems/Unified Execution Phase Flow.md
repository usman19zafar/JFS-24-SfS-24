```mermaid
flowchart LR

    A[Source Tables<br/>LEFT side / RIGHT side] --> B[Phase 1: Matching<br/>(ON clause)]
    B --> C[Phase 2: Preservation<br/>(Join type semantics)]

    C --> C1[INNER<br/>Preserve matched only]
    C --> C2[LEFT<br/>Preserve all LEFT]
    C --> C3[RIGHT<br/>Preserve all RIGHT]
    C --> C4[FULL<br/>Preserve both sides]
    C --> C5[CROSS<br/>Preserve Cartesian]
    C --> C6[SELF<br/>Preserve INNER semantics]

    C --> D[Phase 3: Elimination<br/>(WHERE clause)]

    D --> E1[SAFE<br/>Filters on preserved side]
    D --> E2[COLLAPSE<br/>Filters on NULL‑producing side]
    D --> E3[INVALID<br/>CROSS JOIN with ON]
    D --> E4[NEUTRAL<br/>Filters that do not touch preservation]

    subgraph SFS24[SFS‑24 Structural Semantics]
        C
        C1
        C2
        C3
        C4
        C5
        C6
    end

    subgraph JFS24[JFS‑24 Operational Semantics]
        B
        D
        E1
        E2
        E3
        E4
    end
```
    F[48‑Cell Semantic‑Structural Matrix] --> C
    F --> D
```
