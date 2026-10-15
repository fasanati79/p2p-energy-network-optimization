# Peer-to-Peer (P2P) Electricity Network Design & Smart Pricing

This repository contains the core modeling pipelines, algorithms, and forecasting modules developed for an M.Sc. thesis in Industrial & Systems Engineering at Iran University of Science and Technology (IUST).

## Overview
The project addresses network design, distributed resource allocation, and smart pricing in a localized P2P electricity market with Electric Vehicles (EVs) and Battery Energy Storage Systems (BESS) under uncertainty.

## Pipeline Architecture
1. **Spatial & Temporal Clustering (`yazd_consumption_peak_hour.py`):**
   - Candidate site selection using K-Means clustering and geodesic distance filtering (700m threshold) across Yazd candidate locations.
   - Temporal demand analysis and 4-tier load block identification (Low, Medium, High, Very High) using sliding-window temporal aggregation.

2. **Data-Driven Price Forecasting (`model_sale_price.py`):**
   - Environmental feature integration from NASA POWER and Meteostat (solar irradiance and temperature).
   - Supervised ML models: Linear Regression (baseline), Random Forest Regressor, and XGBoost Regressor.
   - Model selection benchmarked on MAE, RMSE, MAPE, and R².
   - Bounded economic pricing anchored to national grid tariffs (ceiling) and SATBA renewable feed-in tariffs (floor).

3. **Two-Stage Stochastic MILP:**
   - Mixed-Integer Linear Programming formulated in Pyomo.
   - Optimizes long-term investment (charging stations & BESS) and operational dispatch under uncertain renewable generation and EV mobility scenarios.

## Requirements
- Python 3.9+
- `numpy`, `pandas`, `scikit-learn`, `xgboost`, `geopy`, `matplotlib`
- Optimization solver: Gurobi / CPLEX / CBC via Pyomo
