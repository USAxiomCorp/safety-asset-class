# Macro‑Finance Kernel Specification
Level‑0 Domain Standard  
Constitutional Instantiation for Macroeconomic Stability, Monetary Integrity, and Systemic Risk Control

## 1. Purpose
This specification defines the macro‑finance domain instantiation of the RUAX constitutional framework.  
It provides:
• domain‑specific fixed‑point basis (F31)  
• projection rules for inflation, employment, monetary aggregates, and systemic risk  
• hard invariants for monetary stability, sovereign solvency, and contagion control  
• refinement rules for macro‑state convergence  
• audit mappings for macroeconomic traceability  
• cross‑kernel interoperability with finance, energy, logistics, and climate systems  

All macro‑finance kernels must implement this specification exactly.

## 2. Domain State Space
Raw macro‑finance state X includes:
• CPI inflation  
• PPI inflation  
• unemployment rate  
• labor‑force participation  
• GDP growth  
• monetary base (M0)  
• broad money (M2/M3)  
• credit creation  
• sovereign debt levels  
• sovereign yield curve  
• systemic risk indicators  
• interbank liquidity  
• capital flows  
• exchange rates  
• commodity price indices  
• environmental and climate‑linked financial risks  

X is projected into the constitutional state Y via π_macro.

## 3. Fixed‑Point Basis F31
Macro‑finance kernels use a 31‑dimensional basis:

F31 = {
  cpi_inflation,
  ppi_inflation,
  unemployment_rate,
  labor_force_participation,
  gdp_growth_rate,
  monetary_base,
  broad_money_supply,
  credit_creation_rate,
  sovereign_debt_ratio,
  sovereign_yield_curve_slope,
  systemic_risk_index,
  interbank_liquidity_index,
  capital_flow_balance,
  exchange_rate_index,
  commodity_price_index,
  financial_contagion_risk,
  banking_stress_index,
  asset_bubble_risk_index,
  fiscal_balance,
  tax_revenue_rate,
  government_expenditure_rate,
  climate_financial_risk_index,
  environmental_risk_index,
  sensor_health_index,
  data_integrity_index,
  localization_integrity,
  constitutional_reserve,
  convergence_margin,
  dispatch_integrity,
  macro_resilience_index,
  cross_kernel_sync_integrity
}

All components are WAD‑encoded.

## 4. Macro‑Finance Projection Operator π_macro
Projection maps raw macroeconomic data X into Y:

Y = π_macro(X)

Rules:
1. Normalize all macroeconomic
