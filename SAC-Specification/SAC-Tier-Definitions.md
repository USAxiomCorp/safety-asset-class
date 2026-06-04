# Safety Asset Class (SAC) — Tier Definitions
## Foundation for Aligned Intelligence, Truth, and Humanity (FAITH)

The Safety Asset Class (SAC) defines a hierarchical structure of safety tiers that classify autonomous and robotic systems according to their constitutional constraint adherence, refinement behavior, auditability, and hardware‑level enforcement. Each tier represents a mathematically enforceable safety boundary.

This document defines the canonical SAC tiers, their requirements, and their constitutional constraints.

---

## 1. Overview of SAC Tiers

SAC consists of **four primary tiers**, each representing a progressively stronger form of deterministic safety:

- **Tier 0 — Unclassified Systems**  
  No constitutional guarantees. No refinement. No auditability.

- **Tier 1 — Constrained Systems**  
  Basic constitutional boundaries enforced. Limited refinement. Partial auditability.

- **Tier 2 — Deterministic Systems**  
  Full constitutional constraint enforcement. Deterministic refinement. Complete auditability.

- **Tier 3 — Constitutional Systems**  
  Full SAC compliance. Hardware‑enforced constraints. Immutable auditability. Machine‑verifiable law.

Only **Tier 3** systems qualify for **SAC Certification**.

---

## 2. Tier Definitions

### **Tier 0 — Unclassified Systems**
Systems that:
- do not implement constitutional constraints,
- do not support refinement (R³),
- do not produce RAC‑compatible audit logs,
- do not enforce deterministic safety boundaries.

Tier 0 systems **cannot** be certified.

---

### **Tier 1 — Constrained Systems**
Systems that:
- implement basic constitutional constraints,
- support limited refinement sequences,
- produce partial RAC‑compatible logs,
- enforce deterministic boundaries in software only.

Requirements:
- WAD arithmetic for safety‑critical operations,
- RUAX operator compliance for constraint checks,
- partial RAC trace generation.

Tier 1 systems may be used in **non‑critical** environments.

---

### **Tier 2 — Deterministic Systems**
Systems that:
- fully implement constitutional constraints,
- support deterministic R³ refinement,
- produce complete RAC audit logs,
- enforce deterministic boundaries across all safety‑critical operations.

Requirements:
- full WAD arithmetic coverage,
- complete RUAX operator compliance,
- RAC‑compatible trace format,
- MVL constraint enforcement.

Tier 2 systems may be used in **regulated** environments with oversight.

---

### **Tier 3 — Constitutional Systems**
Systems that:
- fully implement constitutional constraints,
- support monotonic R³ refinement,
- produce immutable RAC audit logs,
- enforce constraints at the hardware boundary via CSL,
- satisfy all MVL requirements,
- maintain fixed‑point consistency
