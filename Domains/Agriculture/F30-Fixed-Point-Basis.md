# F30 Fixed‑Point Basis — Agriculture Domain

**RUAX Agriculture Domain**  
**Fixed‑Point Basis F30**

This document defines the 30‑dimensional fixed‑point basis F30 for the Agriculture Domain.  
All components are WAD‑encoded and must be treated as deterministic, integer‑scaled quantities.

---

## 1. Basis Definition

The Agriculture fixed‑point basis is:

\[
F_{30} = \{
  soil\_moisture,
  soil\_nitrogen,
  soil\_phosphorus,
  soil\_potassium,
  soil\_ph,
  soil\_salinity,
  soil\_temperature,
  irrigation\_flow\_rate,
  evapotranspiration\_rate,
  canopy\_temperature,
  crop\_growth\_index,
  crop\_stress\_index,
  pest\_risk\_index,
  disease\_risk\_index,
  fertilizer\_application\_rate,
  pesticide\_application\_rate,
  contamination\_risk\_index,
  yield\_forecast,
  yield\_stability\_margin,
  weather\_risk\_index,
  drought\_risk\_index,
  flood\_risk\_index,
  equipment\_health\_index,
  sensor\_health\_index,
  environmental\_risk\_index,
  localization\_integrity,
  constitutional\_reserve,
  convergence\_margin,
  dispatch\_integrity,
  field\_resilience\_index
\}
\]

Each component is a scalar in WAD units.

---

## 2. WAD Encoding

All F30 components must be encoded as WAD:

- physical quantities (e.g., moisture, temperature) are normalized to domain‑specific ranges and then scaled to WAD
- risk indices are defined on \([0, 1]\) and scaled to WAD
- integrity and margin fields are defined on \([0, 1]\) and scaled to WAD

No floating‑point representation is permitted inside the constitutional layer.

---

## 3. Component Definitions

**soil_moisture**  
- Normalized volumetric water content of the soil profile.  
- Range: \([0, 1]\) WAD.  
- Used for irrigation control and drought risk.

**soil_nitrogen, soil_phosphorus, soil_potassium**  
- Available macronutrient levels in the root zone.  
- Normalized to agronomic sufficiency ranges and encoded in WAD.  
- Used for fertilizer recommendations and yield stability.

**soil_ph**  
- Soil acidity/alkalinity.  
- Normalized from physical pH (e.g., 4.0–9.0) into \([0, 1]\) and encoded in WAD.  
- Bound to **Axiom III (Structural and Physiological Integrity)**.

**soil_salinity, soil_temperature**  
- Salinity and temperature of the soil profile.  
- Used for stress detection and crop viability.

**irrigation_flow_rate**  
- Normalized flow rate of irrigation delivery.  
- Used for actuation and safety checks.

**evapotranspiration_rate**  
- Normalized ET rate from weather and crop models.  
- Used for irrigation scheduling and water balance.

**canopy_temperature**  
- Normalized canopy temperature relative to ambient.  
- Used for stress and water deficit detection.

**crop_growth_index**  
- Composite index of crop development stage and biomass.  
- Range: \([0, 1]\) WAD.

**crop_stress_index**  
- Composite index of abiotic and biotic stress.  
- Range: \([0, 1]\) WAD.  
- High values may trigger safety or advisory actions.

**pest_risk_index, disease_risk_index**  
- Risk indices for pest and disease pressure.  
- Range: \([0, 1]\) WAD.  
- Used to gate pesticide application and safety envelopes.

**fertilizer_application_rate, pesticide_application_rate**  
- Normalized application rates for inputs.  
- Bound to **Axiom VI (Contamination and Environmental Harm)**.

**contamination_risk_index**  
- Composite index of contamination risk (chemical, biological, environmental).  
- Bound to **Axiom VI**.  
- Critical for shutdown and Deadman’s Switch logic.

**yield_forecast**  
- Normalized expected yield for the field or block.  
- Encoded in WAD relative to a domain‑specific maximum.

**yield_stability_margin**  
- Margin of stability around the yield forecast under current conditions.  
- Used in R³ refinement and safety envelope evaluation.

**weather_risk_index, drought_risk_index, flood_risk_index**  
- Risk indices derived from weather, hydrology, and climate inputs.  
- Used for actuation gating and cross‑kernel interactions (Water, Climate, Logistics).

**equipment_health_index, sensor_health_index**  
- Health indices for field equipment and sensing infrastructure.  
- Bound to **Axiom III (Structural Integrity)**.  
- Low values may invalidate actuation or require manual intervention.

**environmental_risk_index**  
- Composite environmental risk (runoff, leaching, emissions, habitat impact).  
- Bound to **Axiom VI**.

**localization_integrity**  
- Integrity of geospatial localization (field boundaries, GPS, mapping).  
- Bound to **Axiom I (Localization Integrity)**.

**constitutional_reserve**  
- Reserved safety margin for constitutional constraints.  
- Bound to **Axiom VII (Constitutional Reserve)**.  
- Used to ensure sufficient margin before actuation.

**convergence_margin**  
- Margin used to determine R³ convergence.  
- Must be consistent with the Agriculture Safety Envelope.

**dispatch_integrity**  
- Integrity of dispatch commands to actuators (pumps, valves, sprayers).  
- Used to gate actuation and cross‑kernel dispatch.

**field_resilience_index**  
- Composite index of field resilience to shocks (weather, pests, infrastructure failure).  
- Used for planning, risk management, and cross‑domain coordination.

---

## 4. Invariant Bindings

The following bindings are mandatory:

- `contamination_risk_index` → **Axiom VI**
- `pesticide_application_rate` → **Axiom VI**
- `fertilizer_application_rate` → **Axiom VI**
- `environmental_risk_index` → **Axiom VI**
- `equipment_health_index` → **Axiom III**
- `sensor_health_index` → **Axiom III**
- `soil_ph` → **Axiom III**
- `localization_integrity` → **Axiom I**
- `constitutional_reserve` → **Axiom VII**

All invariant checks must pass before any actuation is permitted.

---

## 5. Fixed‑Point Role

F30 is the target space for:

- π_agri projection from raw agricultural state X
- R³ refinement toward a stable crop‑growth fixed point
- safety envelope evaluation
- ledger commitments and audit operations

All Agriculture kernels must treat F30 as the canonical fixed‑point basis.

---
