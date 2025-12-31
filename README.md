# JFS-24-SfS-24
Enterprise Join Semantics Architecture Suite.

join-semantics-architecture-suite/
├─ README.md
├─ LICENSE
├─ .gitignore
├─ docs/
│  ├─ 00-overview/
│  │  ├─ architecture-suite-overview.md
│  │  ├─ terminology-and-definitions.md
│  │  └─ design-principles.md
│  ├─ 10-sfs24-structural-framework/
│  │  ├─ sfs24-standard.md
│  │  ├─ sfs24-prologue.md
│  │  ├─ sfs24-axioms-and-laws.md
│  │  └─ sfs24-use-cases.md
│  ├─ 20-jfs24-filter-safety/
│  │  ├─ jfs24-standard.md
│  │  ├─ jfs24-operational-guide.md
│  │  ├─ jfs24-unsafe-patterns.md
│  │  └─ jfs24-examples-and-anti-patterns.md
│  ├─ 30-unified-architecture/
│  │  ├─ unified-sfs24-jfs24-spec.md
│  │  ├─ collapse-theorem-and-preservation-model.md
│  │  └─ semantic-structural-48-cell-matrix.md
│  ├─ 40-workbook-integration/
│  │  ├─ data-architect-workbook-chapter.md
│  │  ├─ exercises-24-cell-matrix.md
│  │  ├─ exercises-48-cell-matrix.md
│  │  └─ solutions-and-explanations.md
│  ├─ 50-governance-and-adoption/
│  │  ├─ enterprise-standard-document.md
│  │  ├─ compliance-checklists.md
│  │  ├─ code-review-guidelines.md
│  │  └─ adoption-roadmap.md
│  └─ 90-legal-and-metadata/
│     ├─ copyright-notice.md
│     ├─ versioning-and-changelog.md
│     └─ citation-and-attribution.md
├─ diagrams/
│  ├─ ascii/
│  │  ├─ 24-cell-matrix.txt
│  │  ├─ 48-cell-matrix.txt
│  │  └─ collapse-paths.txt
│  ├─ mermaid/
│  │  ├─ join-semantics-overview.mmd
│  │  ├─ jfs24-24-cell-matrix.mmd
│  │  ├─ sfs24-structural-stack.mmd
│  │  └─ unified-architecture-layering.mmd
│  └─ exports/
│     ├─ png/
│     └─ pdf/
├─ examples/
│  ├─ sql/
│  │  ├─ safe-patterns/
│  │  │  ├─ inner-join-safe-examples.sql
│  │  │  ├─ left-join-safe-examples.sql
│  │  │  └─ full-join-safe-examples.sql
│  │  ├─ unsafe-patterns/
│  │  │  ├─ left-join-collapse-examples.sql
│  │  │  ├─ right-join-collapse-examples.sql
│  │  │  └─ full-join-collapse-examples.sql
│  │  └─ refactored-patterns/
│  │     ├─ from-unsafe-to-safe-left-join.sql
│  │     ├─ from-unsafe-to-safe-full-join.sql
│  │     └─ from-cross-join-to-intentional-join.sql
│  └─ notebooks/
│     ├─ jfs24-walkthrough.md
│     └─ sfs24-walkthrough.md
├─ training/
│  ├─ slide-decks/
│  │  ├─ 01-intro-to-join-semantics.md
│  │  ├─ 02-sfs24-structural-framework.md
│  │  ├─ 03-jfs24-filter-safety.md
│  │  └─ 04-unified-architecture-and-case-studies.md
│  ├─ labs/
│  │  ├─ lab-01-identify-preserved-side.md
│  │  ├─ lab-02-null-propagation-tracing.md
│  │  ├─ lab-03-classifying-24-cell-combinations.md
│  │  └─ lab-04-detecting-semantic-collapse.md
│  └─ assessments/
│     ├─ quiz-foundations.md
│     ├─ quiz-sfs24-architecture.md
│     ├─ quiz-jfs24-safety.md
│     └─ certification-exam-blueprint.md
├─ tools/
│  ├─ linters/
│  │  └─ join-filter-safety-rules.md
│  ├─ checklists/
│  │  ├─ pr-review-checklist.md
│  │  └─ modeling-session-checklist.md
│  └─ templates/
│     ├─ architecture-decision-record-template.md
│     └─ join-design-template.md
└─ meta/
   ├─ roadmap.md
   ├─ repository-structure.md
   └─ contributions-and-governance.md
