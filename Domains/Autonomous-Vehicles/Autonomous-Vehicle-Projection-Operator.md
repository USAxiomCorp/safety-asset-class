# Autonomous Vehicle Domain — Projection Operator π_av

**RUAX Level‑0 Domain Specification**  
**Autonomous Vehicle Projection Operator (π_av)**

The projection operator π_av maps raw autonomous‑vehicle state \(X\) into the constitutional state \(Y\) in the F31 fixed‑point basis.  
Projection must be deterministic, WAD‑encoded, invariant‑compatible, and admissible under the AV Purity Gate.

---

# 1. Purpose

The projection operator ensures:

- raw perception, planning, and control data becomes constitutional data  
- all values are normalized and WAD‑encoded  
- all F31 components are representable  
- all constitutional invariants are computable  
- all safety‑critical fields are admissible  
- all purity‑gate conditions are evaluable  

No AV kernel may operate without π_av.

---

# 2. Formal Definition

Projection is defined as:

\[
Y = \pi_{av}(X)
\]

Where:

- \(X\) = raw AV state  
- \(Y\) = constitutional state in F31  
- all values in \(Y\) must be WAD‑encoded  
- all values must satisfy representability and admissibility  

Projection must be:

- total  
- deterministic  
- finite  
- monotonic toward safety  

---

# 3. Projection Stages

π_av consists of three stages:

- **[Normalization](ca://s?q=Explain_AV_Normalization_Stage)**  
- **[Axiom Binding](ca://s?q=Explain_AV_Axiom_Binding)**  
- **[WAD Encoding](ca://s?q=Explain_AV_WAD_Encoding)**  

---

# 4. Stage 1 — Normalization

\[
x_i^{norm} = \frac{x_i - min_i}{max_i - min_i}
\]

Out‑of‑range or missing → **projection rejected**.

---

# 5. Stage 2 — Axiom Binding

Each normalized component binds to:

- **Axiom I** — localization_integrity, ego_position_error  
- **Axiom III** — steering_angle, friction_estimate, sensor_health_index, control_surface_health  
- **Axiom VI** — collision_risk_index, time_to_collision_min, lane_offset, environmental_risk_index, pedestrian_proximity, vehicle_proximity  
- **Axiom VII** — constitutional_reserve  

Binding failure → **projection rejected**.

---

# 6. Stage 3 — WAD Encoding

\[
Y_i = \lfloor x_i^{norm} \cdot S_i \rfloor
\]

Non‑encodable → **projection rejected**.

---

# 7. Projection Requirements

- deterministic  
- monotonic toward safety  
- invariant‑compatible  
- purity‑gate compatible  
- ledger‑representable  

---

# 8. Projection Failure Classes

- **[Class I — Missing Inputs](ca://s?q=Explain_AV_Projection_Missing_Inputs)**  
- **[Class II — Axiom Binding Failure](ca://s?q=Explain_AV_Axiom_Binding_Failure)**  
- **[Class III — Encoding Failure](ca://s?q=Explain_AV_Encoding_Failure)**  

---

# 9. Safety‑Critical Projection Fields

- collision_risk_index  
- time_to_collision_min  
- lane_offset  
- friction_estimate  
- sensor_health_index  
- localization_integrity  
- control_surface_health  

Invalid → **projection rejected**.

---

# 10. Summary

π_av:

- transforms raw AV data into constitutional state  
- enforces axiom bindings  
- ensures WAD determinism  
- guarantees invariant and purity‑gate compatibility  
- supports safe refinement and actuation  
- ensures ledger‑ready representation  

All AV kernels must implement π_av exactly.

---
