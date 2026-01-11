# Synthetic Nonprofit Forecasting Model (Math 499 Capstone)

End-to-end forecasting workflow for nonprofit revenue and donor activity using a synthetic dataset designed to resemble real donor management systems. The project covers data generation and validation, exploratory analysis, model training, time-aware validation, and forecast visualization.

## Why this project
Nonprofits rely on recurring gifts and sponsorship-style commitments. Accurate forecasting supports Finance and Philanthropy teams in planning staffing, programs, and cash flow. This project demonstrates how to:
- validate time-series data quality,
- avoid data leakage and mis-specified time splits,
- compare baseline and statistical forecasting approaches,
- communicate results clearly using business-facing visuals.

## Dataset (Synthetic)
**Grain:** Monthly totals by fiscal month  
**Key fields:** Fiscal Year, Fiscal Month, Active Start, New, Cancellations, Terminations, Active End, Revenue  
**Notes:** Data are fully synthetic and intended for portfolio demonstration. Generation logic reflects common donor lifecycle dynamics, including acquisition, churn, and seasonality.

## Approach
1. **Data preparation**
   - Validate time index (no missing months, consistent ordering)
   - Sanity checks on totals, continuity, and outliers
2. **Feature engineering**
   - Lagged variables and rolling statistics where appropriate
   - Seasonal indicators (calendar and fiscal month)
3. **Models**
   - Baselines: seasonal naïve, moving average
   - Statistical: SARIMA / SARIMAX
4. **Validation**
   - Strict time-based train/validation split
   - Metrics: MAE and RMSE
   - Residual diagnostics for bias and autocorrelation

## Results
Key outputs are saved in `visuals/`.

- **Power BI — Historical Actuals**  
  Shows synthetic revenue and donor activity trends with realistic seasonality and growth patterns.
  
  ![Synthetic historical actuals](visuals/PowerBI%20Synthetic%20Historical%20Acutals.png)

- **Power BI — Projection Model**  
  Displays forward projections from the selected time-series model with historical context.
  
  ![PowerBI synthetic projection model](visuals/PowerBI%20Synthetic%20Projection%20Model.png)

**Best model:** SARIMAX  
**Headline performance:** Stable seasonal capture with lower error than baseline models on the holdout period.

## Repository structure
- `notebooks/` — analysis and modeling notebooks (intended to be run sequentially)
- `data/` — synthetic datasets and generation outputs
- `visuals/` — exported charts and tables used in this README
- `docs/` — methodology notes and capstone write-up

## How to run

### Option A — Notebooks
1. Create and activate a virtual environment:
   ```bash
   python -m venv .venv
   source .venv/bin/activate  # macOS/Linux
   # .venv\Scripts\activate   # Windows
   pip install -r requirements.txt
