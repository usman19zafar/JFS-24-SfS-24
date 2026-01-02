# Collapse Theorem & Preservation Model  
### Unified SFS‑24 + JFS‑24 Architecture  
**Version 1.0 — 2025**  
**Author: Usman Zafar**

---

## 1. Purpose

This document defines the **Collapse Theorem** and the **Preservation Model**, the two foundational concepts that unify:

- **SFS‑24** (structural semantics)  
- **JFS‑24** (operational semantics)  

These concepts explain *why* joins collapse, *how* preservation works, and *what* rules govern the stability of relational semantics.

This file is part of the **Unified Architecture** section.

---

## 2. The Preservation Model (SFS‑24 Core)

### 2.1 Definition

A join defines a **preservation contract**:

> **A join must preserve the rows it promises to preserve.**

Each join type has a structural obligation:

| Join Type       |     Must Preserve        |
|-----------------|--------------------------|
| INNER           | matched rows only        |
| LEFT            |     all LEFT rows        |
| RIGHT           |    all RIGHT rows        |
| FULL            | all rows from both sides |
| CROSS           | Cartesian product        |
| SELF            | INNER semantics          |

Preservation is **not optional**.  
It is the structural identity of the join.

---

### 2.2 Preservation and NULL‑Propagation

NULLs produced by joins are **structural signals** indicating:

- missing relationships  
- incomplete dimensions  
- orphaned facts  
- preservation boundaries  

**Rule:**  
> NULL‑extended rows must survive on the preserved side.

If they do not survive, the join collapses.

---

### 2.3 Preservation Invariants

The Preservation Model defines three invariants:

1. **Preservation must not be violated**  
2. **NULL‑extended rows must not be eliminated**  
3. **Join semantics must remain stable**  

These invariants form the structural backbone of SFS‑24.

---

## 3. The Collapse Theorem (Unified SFS‑24 + JFS‑24)

### 3.1 Formal Statement

> **A join collapses when a filter eliminates NULL‑extended rows on the preserved side.**

This is the **Collapse Theorem**.

It is the single most important rule in the entire architecture.

---

### 3.2 Collapse Mechanism

Collapse occurs when:

- WHERE eliminates NULL‑extended rows  
- ON is misused to simulate INNER JOIN behavior  
- CROSS JOIN is given an ON condition  
- FULL JOIN is filtered asymmetrically  
- NULL‑sensitive filters are applied to the NULL‑producing side  

Collapse is not a runtime error.  
It is a **semantic failure mode**.

---

### 3.3 Collapse Outcomes

Depending on the join type, collapse results in:

| Original Join          | Collapse Result                  |
|------------------------|----------------------------------|
| LEFT                   |    INNER                         |
| RIGHT                  | INNER                            |
| FULL                   | LEFT / RIGHT / INNER             |
| CROSS                  | INNER‑like behavior              |
| SELF                   | No collapse (behaves like INNER) |

Collapse destroys the join’s structural identity.

---

## 4. Collapse Patterns (JFS‑24 Core)

The Collapse Theorem manifests through six operational patterns:

1. **LEFT JOIN + WHERE on RIGHT**  
2. **RIGHT JOIN + WHERE on LEFT**  
3. **FULL JOIN + WHERE on LEFT**  
4. **FULL JOIN + WHERE on RIGHT**  
5. **CROSS JOIN + ON (Left)**  
6. **CROSS JOIN + ON (Right)**  

These patterns must be prohibited in code review.

---

## 5. Unified Collapse Model

The unified model integrates structural and operational collapse:

### **5.1 Structural Collapse (SFS‑24)**  
Occurs when preservation is violated.

### **5.2 Operational Collapse (JFS‑24)**  
Occurs when WHERE eliminates NULL‑extended rows.

### **5.3 Unified Collapse Doctrine**

> **Collapse is the destruction of the join contract.**

If preservation is violated, the join is no longer the join it claims to be.

---

## 6. Collapse Detection Rules

To detect collapse:

1. Identify the **preserved side**  
2. Identify the **NULL‑producing side**  
3. Identify filter placement (ON vs WHERE)  
4. Identify filter type (NULL‑sensitive vs NULL‑neutral)  
5. Validate against the **48‑cell matrix**  

If a filter eliminates NULL‑extended rows on the preserved side → **collapse**.

---

## 7. Preservation‑Safe Patterns

### 7.1 Filter on Preserved Side
```sql
LEFT JOIN dim d ON f.key = d.key
WHERE f.status = 'ACTIVE';

7.2 Filter in ON Clause
sql
LEFT JOIN dim d
  ON f.key = d.key
 AND d.is_current = 1;

7.3 Use COALESCE for FULL JOIN
sql
WHERE COALESCE(f.flag, d.flag) = 'Y'

8. Collapse‑Unsafe Patterns

8.1 LEFT JOIN Collapse
sql
WHERE d.category = 'A'

8.2 FULL JOIN Collapse
sql
WHERE d.key IS NOT NULL

8.3 CROSS JOIN Collapse
sql
CROSS JOIN dim d ON f.key = d.key

9. Relationship to the 48‑Cell Matrix
The Collapse Theorem is encoded directly into the:

Semantic‑Structural 48‑Cell Matrix  

Every collapse scenario corresponds to a COLLAPSE or INVALID cell.

10. Governance Requirements
To comply with the unified architecture:

All joins must declare preservation intent

All filters must declare operational intent

All SQL must be validated against the 48‑cell matrix

All collapse patterns must be prohibited

All code reviews must apply SFS‑24 + JFS‑24 rules

11. Copyright
© 2025 Usman Zafar. All rights reserved.
This document is proprietary intellectual property.
