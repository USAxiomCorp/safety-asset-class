# Autonomous Vehicle Domain — Invariants

**RUAX Level‑0 Domain Specification**  
**Autonomous Vehicle Invariant System (INV_av)**

The Autonomous Vehicle invariant system defines the constitutional safety conditions that must hold for every AV state \(Y\) in the F31 basis.  
All invariants must be:

- WAD‑decidable  
- deterministic  
- monotonic toward safety  
- axiom‑bound  
- purity‑gate compatible  
- actuation‑blocking on failure  

No AV kernel may actuate unless **all invariants pass**.

---

# 1. Purpose

The AV invariant system ensures:

- collision‑avoidance  
- lane‑keeping stability  
- friction and traction safety  
- perception and localization integrity  
- actuator health  
- environmental risk control  
- constitutional reserve protection  

These invariants form the **constitutional safety envelope** for autonomous driving.

---

# 2. Formal Definition

An invariant is a function:

\[
inv_i : F_{31} \rightarrow \{pass, fail\}
\]

The AV state is admissible if:

\[
INV_{av}(Y) = pass \iff \forall i,\; inv_i(Y) = pass
\]

If any invariant fails → **actuation blocked** and **Deadman’s Switch** evaluated.

---

# 3. Invariant List (F31‑Bound)

Each invariant begins with a **Guided Link**, as required.

- **[inv_collision_risk](ca://s?q=Explain_AV_Collision_Risk_Invariant)** —  
  \[
  collision\_risk\_index \le R_{max}
  \]
  with \(R_{max} = 0.20\).

- **[inv_ttc_min](ca://s?q=Explain_AV_TTC_Invariant)** —  
  \[
  time\_to\_collision\_{min} \ge TTC_{min}
  \]
  with \(TTC_{min} = 2.0 \text{ seconds (WAD‑scaled)}\).

- **[inv_lane_offset](ca://s?q=Explain_AV_Lane_Offset_Invariant)** —  
  \[
  |lane\_offset| \le L_{max}
  \]
  with \(L_{max} = 0.30 \text{ m (WAD‑scaled)}\).

- **[inv_steering_angle](ca://s?q=Explain_AV_Steering_Angle_Invariant)** —  
  steering_angle must be within actuator‑safe bounds.

- **[inv_friction_estimate](ca://s?q=Explain_AV_Friction_Invariant)** —  
  friction_estimate must exceed traction threshold.

- **[inv_sensor_health](ca://s?q=Explain_AV_Sensor_Health_Invariant)** —  
  \[
  sensor\_health\_index \ge 0.80
  \]

- **[inv_localization_integrity](ca://s?q=Explain_AV_Localization_Integrity_Invariant)** —  
  \[
  localization\_integrity \ge 0.95
  \]

- **[inv_environmental_risk](ca://s?q=Explain_AV_Environmental_Risk_Invariant)** —  
  \[
  environmental\_risk\_index \le 0.25
  \]

- **[inv_pedestrian_proximity](ca://s?q=Explain_AV_Pedestrian_Proximity_Invariant)** —  
  pedestrian_proximity must remain below hazard threshold.

- **[inv_vehicle_proximity](ca://s?q=Explain_AV_Vehicle_Proximity_Invariant)** —  
  vehicle_proximity must remain below hazard threshold.

- **[inv_roll_pitch_yaw_stability](ca://s?q=Explain_AV_Stability_Invariant)** —  
  roll, pitch, yaw stability indices must exceed minimum safe values.

- **[inv_slip_ratio](ca://s?q=Explain_AV_Slip_Ratio_Invariant)** —  
  slip_ratio must remain within traction envelope.

- **[inv_slip_angle](ca://s?q=Explain_AV_Slip_Angle_Invariant)** —  
  slip_angle must remain within stability envelope.

- **[inv_control_surface_health](ca://s?q=Explain_AV_Control_Surface_Health_Invariant)** —  
  control_surface_health must be ≥ 0.85.

- **[inv_constitutional_reserve](ca://s?q=Explain_AV_Constitutional_Reserve_Invariant)** —  
  \[
  constitutional\_reserve \ge 0.10
  \]

---

# 4. Axiom Bindings

- **Axiom I** — localization_integrity, ego_position_error  
- **Axiom III** — steering_angle, friction_estimate, sensor_health_index, control_surface_health  
- **Axiom VI** — collision_risk_index, time_to_collision_min, lane_offset, environmental_risk_index, pedestrian_proximity, vehicle_proximity  
- **Axiom VII** — constitutional_reserve  

Binding failure → invariant failure.

---

# 5. WAD‑Decidability

All invariants must be:

- integer‑scaled  
- bounded  
- monotonic  
- computable in finite steps  
- free of floating‑point operations  

Undecidable → **actuation blocked**.

---

# 6. Safety Envelope Integration

\[
\|Y - Y^*\| \le A_{max}
\]

with:

\[
A_{max} = 10^{-4} \text{ WAD units}
\]

Envelope violation → **Deadman’s Switch**.

---

# 7. Ledger Requirements

Every invariant evaluation must be logged:

- invariant name  
- pass/fail  
- threshold  
- measured value  
- timestamp  
- vehicle_id  
- route_id  

Missing logs → **ledger invalid**.

---

# 8. Summary

The AV invariant system:

- enforces collision‑avoidance  
- ensures lane‑keeping and stability  
- protects against environmental and perception failures  
- guarantees actuator and sensor integrity  
- preserves constitutional reserve  
- ensures WAD‑decidable, deterministic safety  

All AV kernels must implement INV_av exactly.

---
