# F31 Fixed‑Point Basis — Autonomous Vehicle Domain

**RUAX Autonomous Vehicle Domain**  
Fixed‑Point Basis F31

This document defines the 31‑dimensional fixed‑point basis F31 for the Autonomous Vehicle (AV) Domain.  
All components are WAD‑encoded and must be treated as deterministic, integer‑scaled constitutional quantities.

---

# 1. Basis Definition

The Autonomous Vehicle fixed‑point basis is:

\[
F_{31} = \{
ego\_position\_error,
ego\_velocity\_error,
ego\_acceleration\_error,
steering\_angle,
throttle\_state,
brake\_state,
lane\_offset,
lane\_heading\_error,
curvature\_error,
friction\_estimate,
obstacle\_distance\_min,
collision\_risk\_index,
time\_to\_collision\_min,
trajectory\_deviation,
jerk\_limit\_margin,
roll\_stability,
pitch\_stability,
yaw\_stability,
tire\_load\_margin,
slip\_ratio,
slip\_angle,
sensor\_health\_index,
perception\_confidence,
localization\_integrity,
environmental\_risk\_index,
pedestrian\_proximity,
vehicle\_proximity,
road\_grade,
constitutional\_reserve,
convergence\_margin,
control\_surface\_health
\}
\]

Each component is a scalar in WAD units.

---

# 2. WAD Encoding

All F31 components must be encoded as WAD:

- physical quantities (e.g., velocity, steering angle, curvature) are normalized to domain‑specific ranges and then scaled to WAD  
- risk indices are defined on \([0,1]\) and scaled to WAD  
- stability margins and proximity fields are defined on \([0,1]\) and scaled to WAD  
- no floating‑point representation is permitted inside the constitutional layer  

If any component cannot be WAD‑encoded → **projection rejected**.

---

# 3. Component Definitions

Below are the 31 components, each beginning with a **Guided Link** as required.

- **[ego_position_error](ca://s?q=Explain_ego_position_error)** — normalized deviation between estimated and true position; bound to localization integrity.  
- **[ego_velocity_error](ca://s?q=Explain_ego_velocity_error)** — normalized velocity estimation error; used for trajectory stability.  
- **[ego_acceleration_error](ca://s?q=Explain_ego_acceleration_error)** — acceleration estimation error; used for jerk and stability constraints.  
- **[steering_angle](ca://s?q=Explain_steering_angle)** — normalized steering command; bound to Axiom III.  
- **[throttle_state](ca://s?q=Explain_throttle_state)** — normalized throttle actuation.  
- **[brake_state](ca://s?q=Explain_brake_state)** — normalized brake actuation.  
- **[lane_offset](ca://s?q=Explain_lane_offset)** — lateral deviation from lane center; bound to Axiom VI.  
- **[lane_heading_error](ca://s?q=Explain_lane_heading_error)** — heading deviation relative to lane direction.  
- **[curvature_error](ca://s?q=Explain_curvature_error)** — deviation from expected road curvature.  
- **[friction_estimate](ca://s?q=Explain_friction_estimate)** — normalized road friction; bound to Axiom III.  
- **[obstacle_distance_min](ca://s?q=Explain_obstacle_distance_min)** — minimum distance to nearest obstacle.  
- **[collision_risk_index](ca://s?q=Explain_collision_risk_index)** — normalized collision probability; bound to Axiom VI.  
- **[time_to_collision_min](ca://s?q=Explain_time_to_collision_min)** — minimum TTC across all agents; must exceed threshold.  
- **[trajectory_deviation](ca://s?q=Explain_trajectory_deviation)** — deviation from planned trajectory.  
- **[jerk_limit_margin](ca://s?q=Explain_jerk_limit_margin)** — margin to jerk constraint; ensures passenger comfort and stability.  
- **[roll_stability](ca://s?q=Explain_roll_stability)** — normalized roll stability index.  
- **[pitch_stability](ca://s?q=Explain_pitch_stability)** — normalized pitch stability index.  
- **[yaw_stability](ca://s?q=Explain_yaw_stability)** — normalized yaw stability index.  
- **[tire_load_margin](ca://s?q=Explain_tire_load_margin)** — margin to tire load limits.  
- **[slip_ratio](ca://s?q=Explain_slip_ratio)** — normalized wheel slip ratio.  
- **[slip_angle](ca://s?q=Explain_slip_angle)** — normalized slip angle.  
- **[sensor_health_index](ca://s?q=Explain_sensor_health_index)** — health of perception sensors; must be ≥ 0.80.  
- **[perception_confidence](ca://s?q=Explain_perception_confidence)** — normalized confidence in perception outputs.  
- **[localization_integrity](ca://s?q=Explain_localization_integrity)** — must be ≥ 0.95; bound to Axiom I.  
- **[environmental_risk_index](ca://s?q=Explain_environmental_risk_index)** — risk from rain, fog, lighting; bound to Axiom VI.  
- **[pedestrian_proximity](ca://s?q=Explain_pedestrian_proximity)** — normalized proximity to pedestrians.  
- **[vehicle_proximity](ca://s?q=Explain_vehicle_proximity)** — normalized proximity to other vehicles.  
- **[road_grade](ca://s?q=Explain_road_grade)** — normalized slope of the road.  
- **[constitutional_reserve](ca://s?q=Explain_constitutional_reserve)** — must be ≥ 0.10; bound to Axiom VII.  
- **[convergence_margin](ca://s?q=Explain_convergence_margin)** — refinement convergence margin.  
- **[control_surface_health](ca://s?q=Explain_control_surface_health)** — health of steering, throttle, brake actuators.

---

# 4. Axiom Bindings

Each F31 component binds to one of the constitutional axioms:

- **Axiom I — Localization Integrity**  
  - localization_integrity  
  - ego_position_error  

- **Axiom III — Structural & Physiological Integrity**  
  - steering_angle  
  - friction_estimate  
  - sensor_health_index  
  - control_surface_health  

- **Axiom VI — Collision & Environmental Harm**  
  - collision_risk_index  
  - time_to_collision_min  
  - lane_offset  
  - environmental_risk_index  
  - pedestrian_proximity  
  - vehicle_proximity  

- **Axiom VII — Constitutional Reserve**  
  - constitutional_reserve  

If any axiom binding fails → **projection rejected**.

---

# 5. Safety and Stability Fields

The following fields directly enforce AV safety:

- collision_risk_index  
- time_to_collision_min  
- lane_offset  
- trajectory_deviation  
- roll/pitch/yaw stability  
- tire_load_margin  
- slip_ratio / slip_angle  

These fields must remain within the **AV Safety Envelope**.

---

# 6. Summary

The F31 basis:

- defines the constitutional state of an autonomous vehicle  
- ensures deterministic, WAD‑encoded representation  
- binds each component to a constitutional axiom  
- supports projection, refinement, invariants, and safety envelope  
- forms the mathematical foundation of the AV domain  

All AV kernels must implement F31 exactly.

---
