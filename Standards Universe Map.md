```mermaid
flowchart TD

    %% Meta Layer
    FA[Foundational Assumptions<br/>"Physics / First Principles"]

    %% Architecture Layer
    DAIS[DAIS‑10<br/>"System Architecture"]

    %% Assurance Layer
    QFIM[QFIM‑10<br/>"Quality & Inspection Model"]

    %% Flow Layer
    DIFS[DIFS‑10<br/>"Data Flow Standard"]

    %% Safety Layer
    SFS[SFS‑24<br/>"Safety Filter Standard"]

    %% Join Layer
    JFS[JFS‑24<br/>"Join Framework Standard"]

    %% Relationships
    FA --> DAIS
    FA --> QFIM
    FA --> DIFS
    FA --> SFS
    FA --> JFS

    DAIS --> QFIM
    DAIS --> DIFS
    DAIS --> SFS
    DAIS --> JFS

    DIFS --> QFIM
    DIFS --> SFS

    JFS --> QFIM
    JFS --> SFS

    SFS --> QFIM
```
