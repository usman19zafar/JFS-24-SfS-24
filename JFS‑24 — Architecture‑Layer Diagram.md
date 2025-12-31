flowchart TD

    A[**JFS‑24 Join‑Filter Safety Standard**] --> B[Layer 1: Execution‑Phase Semantics]
    A --> C[Layer 2: Filter‑Side Safety Rules]
    A --> D[Layer 3: Unsafe Patterns]
    A --> E[Layer 4: Join‑Filter Matrix (24‑Cell)]
    A --> F[Layer 5: Operational Safety Doctrine]

    B --> B1[ON = pre‑join matching]
    B --> B2[WHERE = post‑join elimination]
    B --> B3[WHERE kills NULLs]
    B --> B4[ON controls matching]

    C --> C1[Safe: filter on preserved side]
    C --> C2[Unsafe: filter on NULL‑producing side]
    C --> C3[Neutral: ON filters on preserved side]
    C --> C4[Invalid: ON filters on CROSS JOIN]

    D --> D1[LEFT JOIN + RIGHT WHERE]
    D --> D2[RIGHT JOIN + LEFT WHERE]
    D --> D3[FULL JOIN + LEFT WHERE]
    D --> D4[FULL JOIN + RIGHT WHERE]
    D --> D5[CROSS JOIN + LEFT ON]
    D --> D6[CROSS JOIN + RIGHT ON]

    E --> E1[SAFE / UNSAFE / NEUTRAL / INVALID]
    E --> E2[24‑Cell Join‑Filter Classification]

    F --> F1["Filters must preserve join contracts"]
    F --> F2["Unsafe filters cause semantic collapse"]
    F --> F3["Join semantics and filter semantics must align"]
