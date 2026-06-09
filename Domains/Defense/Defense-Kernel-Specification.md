# Defense Kernel Specification
Level‑0 Domain Standard  
Constitutional Instantiation for Defense Sensing, Threat Evaluation, and Command‑and‑Control

## 1. Purpose
This specification defines the defense domain instantiation of the RUAX constitutional framework.  
It provides:
• domain‑specific fixed‑point basis (F34)  
• projection rules for sensing, threat evaluation, and command‑and‑control  
• hard invariants for targeting envelopes, safety, and escalation control  
• refinement rules for threat‑state convergence  
• audit mappings for defense traceability  
• cross‑kernel interoperability with aerospace, energy, logistics, and urban systems  

All defense kernels must implement this specification exactly.

## 2. Domain State Space
Raw defense state X includes:
• radar, EO/IR, RF, and SIGINT sensor outputs  
• fused target tracks  
• threat classification  
• engagement envelopes  
• blue‑force positions  
• no‑fire zones  
• rules‑of‑engagement (ROE) parameters  
• communication integrity  
• environmental conditions  
• escalation‑risk indicators  

X is projected into the constitutional state Y via π_defense.

## 3. Fixed‑Point Basis F34
Defense kernels use a 34‑dimensional basis:

F34 = {
  target_position_error,
  target_velocity_error,
  target_acceleration_error,
  threat_classification_index,
  threat_confidence,
  engagement_feasibility,
  no_fire_zone_distance,
  blue_force_proximity,
  collateral_risk_index,
  escalation_risk_index,
  sensor_health_index,
  sensor_fusion_integrity,
  communication_integrity,
  jamming_risk_index,
  spoofing_risk_index,
  environmental_r
