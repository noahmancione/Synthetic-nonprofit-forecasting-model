# Synthetic Nonprofit Forecasting Model (Math 499 Capstone)

End-to-end forecasting workflow for nonprofit revenue and donor activity using a synthetic dataset designed to resemble real donor systems. Includes data generation/cleaning, exploratory analysis, model training, validation, and forecast visualization.

# Why this project
Nonprofits rely on recurring gifts and sponsorship-style commitments; forecasting helps Finance and Philanthropy plan staffing, programs, and cashflow. This project demonstrates how to:
- validate time-series data quality,
- avoid leakage and mis-specified time splits,
- compare forecasting approaches,
- communicate results clearly with business-facing visuals.

## Dataset (Synthetic)
**Grain:** [e.g., monthly totals by fiscal month]  
**Key fields:** [Fiscal Year, Fiscal Month, Active Start, New, Cancellations, Terminations, Active End, Revenue, etc.]  
**Notes:** Data are synthetic and intended for portfolio demonstration; logic reflects typical donor lifecycle dynamics (acquisition, churn, seasonality).

## Approach
1. **Data preparation**
   - Clean and validate time index (no missing months, consistent ordering)
   - Sanity checks: totals, monotonic constraints (where applicable), outliers
2. **Feature engineering**
   - Lag features / rolling averages (where used)
   - Seasonal indicators (month, fiscal month)
3. **Models**
   - Baselines: seasonal naive / moving average
   - Statistical: SARIMA/SARIMAX
   - Additional: [Prophet / other], if included
4. **Validation**
   - Time-based train/validation split (no random split)
   - Metrics: MAE, RMSE, MAPE (as appropriate)
   - Residual diagnostics (autocorrelation, bias checks)

## Results
Key outputs are saved in `visuals/`.

- **Forecast vs Actual**
  - ![Forecast vs Actual](visuals/forecast_vs_actual.png)

- **Error Metrics Summary**
  - ![Metrics](visuals/metrics_table.png)

**Best model:** [SARIMAX / SARIMA / etc.]  
**Headline performance:** [e.g., RMSE = X on holdout period; stable seasonal capture]

## Repository structure
- `notebooks/` — analysis and modeling notebooks (run in order)
- `data/` — synthetic datasets (or generation outputs)
- `visuals/` — exported charts and tables for the README
- `docs/` — methodology notes / capstone write-up

## How to run
### Option A — Notebooks
1. Create environment:
   ```bash
   python -m venv .venv
   source .venv/bin/activate  # macOS/Linux
   # .venv\Scripts\activate   # Windows
   pip install -r requirements.txt
