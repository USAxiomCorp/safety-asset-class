# Autonomous Vehicle Domain — Purity Gate

**RUAX Level‑0 Domain Specification**  
**Autonomous Vehicle Purity Gate (PG_av)**

The Autonomous Vehicle Purity Gate defines the constitutional admissibility conditions that must hold for any AV state transition.  
The purity gate ensures that:

- projection is admissible  
- invariants are decidable  
- refinement is safe  
- actuation is permissible  
- no impurity, corruption, or undefined behavior enters the constitutional layer  

If the purity gate fails → **all refinement and actuation are blocked**.

---

# 1. Purpose

The AV Purity Gate ensures:

- no undefined or missing values enter the constitutional layer  
- no floating‑point values bypass WAD encoding  
- no invariant becomes undecidable  
- no safety envelope violation is allowed  
- no cross‑kernel interaction occurs without integrity  
- no refinement step increases risk  
- no actuation occurs under impurity  

PG_av is the **constitutional firewall** of the AV domain.

---

# 2. Formal Definition

The purity gate is defined as:

\[
PG_{av}(Y, Y') =
\begin{cases}
1 & \text{if all purity conditions hold} \\
0 & \text{otherwise}
\end{cases}
\]

Where:

- \(Y\) = current constitutional state  
- \(Y'\) = refined constitutional state  
- both must be WAD‑encoded  
- both must satisfy invariant admissibility  

---

# 3. Purity Conditions

Each condition begins with a **Guided Link**, as required.

- **[pg_projection_admissible](ca://s?q=Explain_AV_PG_Projection_Admissible)** —  
  π_av must succeed with no missing or undefined values.

- **[pg_wad_encoding](ca://s?q=Explain_AV_PG_WAD_Encoding)** —  
  All components must be integer‑scaled WAD values.

- **[pg_invariant_decidability](ca://s?q=Explain_AV_PG_Invariant_Decidability)** —  
  All invariants must be computable in finite steps.

- **[pg_invariant_pass](ca://s?q=Explain_AV_PG_Invariant_Pass)** —  
  All invariants must pass before actuation.

- **[pg_safety_envelope](ca://s?q=Explain_AV_PG_Safety_Envelope)** —  
  \[
  \|Y - Y^*\| \le A_{max}
  \]
  with \(A_{max} = 10^{-4}\).

- **[pg_contraction](ca://s?q=Explain_AV_PG_Contraction)** —  
  R³ must satisfy contraction:
  \[
  \|Y' - Y^*\| \le 0.85 \cdot \|Y - Y^*\|
  \]

- **[pg_risk_monotonicity](ca://s?q=Explain_AV_PG_Risk_Monotonicity)** —  
  Risk must not increase:
  \[
  risk(Y') \le risk(Y)
  \]

- **[pg_actuator_bounds](ca://s?q=Explain_AV_PG_Actuator_Bounds)** —  
  Steering, throttle, brake must remain within safe limits.

- **[pg_sensor_integrity](ca://s?q=Explain_AV_PG_Sensor_Integrity)** —  
  sensor_health_index ≥ 0.80.

- **[pg_localization_integrity](ca://s?q=Explain_AV_PG_Localization_Integrity)** —  
  localization_integrity ≥ 0.95.

- **[pg_cross_kernel_integrity](ca://s?q=Explain_AV_PG_Cross_Kernel_Integrity)** —  
  dispatch_integrity ≥ 0.90.

- **[pg_constitutional_reserve](ca://s?q=Explain_AV_PG_Constitutional_Reserve)** —  
  constitutional_reserve ≥ 0.10.

If any purity condition fails → **PG_av = 0**.

---

# 4. Purity Failure Classes

Purity failures fall into three classes:

- **[Class I — Representability Failure](ca://s?q=Explain_AV_PG_Representability_Failure)**  
  Missing, undefined, or non‑WAD values.

- **[Class II — Safety Failure](ca://s?q=Explain_AV_PG_Safety_Failure)**  
  Invariant or envelope violation.

- **[Class III — Convergence Failure](ca://s?q=Explain_AV_PG_Convergence_Failure)**  
  Contraction or risk monotonicity failure.

Each class triggers a different audit path.

---

# 5. Deadman’s Switch Integration

If PG_av = 0 → the Deadman’s Switch must evaluate:

- collision risk  
- TTC  
- lane offset  
- actuator health  
- sensor integrity  
- localization integrity  

If Deadman’s Switch fails → **shutdown**.

---

# 6. Ledger Requirements

Each purity‑gate evaluation must be logged:

- purity‑gate status  
- failure class (if any)  
- failing component  
- measured value  
- threshold  
- timestamp  
- vehicle_id  
- route_id  

Missing purity‑gate logs → **ledger invalid**.

---

# 7. Summary

The AV Purity Gate:

- enforces constitutional admissibility  
- blocks unsafe or undefined behavior  
- ensures WAD determinism  
- protects invariants and safety envelope  
- guarantees contraction and risk monotonicity  
- anchors cross‑kernel trust  
- integrates with Deadman’s Switch  
- ensures regulator‑grade auditability  

All AV kernels must implement PG_av exactly.

---
