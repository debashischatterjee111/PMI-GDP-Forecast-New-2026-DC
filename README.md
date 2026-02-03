# PMI-GDP-Forecast-New-2026-DC


# PMI Components and GDP Forecasting (2012Q2–2022Q1)

This repository contains the data, code, and reproducible outputs for an empirical study asking:

> Which PMI survey components—forward-looking expectations, current output/new orders, employment, or input/output price signals—contain the most economically meaningful predictive content for the future path of real GDP?

The workflow compares the forecasting value of individual PMI components and joint models, with robust (HAC/Newey–West) inference and expanding-window out-of-sample evaluation.

---

## Repository structure

A recommended layout (matches the ZIP output structure used by the pipeline):

├── data/
│ ├── PMI-Final data.xlsx
│ └── PMI-SS(RBI).xlsx
├── code/
│ └── run_pmi_gdp_forecast.py # main reproducible script (Colab/Python)
├── outputs/
│ ├── run_YYYYMMDD_HHMMSS/
│ │ ├── figures/
│ │ ├── tables/
│ │ └── reports/
│ └── run_YYYYMMDD_HHMMSS.zip


---

## Data

### Primary dataset: `PMI-Final data.xlsx`
Quarterly observations aligned to GDP, including PMI components:
- Future Output (expectations)
- Output
- New Orders
- Employment
- Input Prices
- Output Prices  
plus GDP growth, inflation measures, and a COVID dummy.

### Secondary dataset: `PMI-SS(RBI).xlsx`
Quarterly series with related PMI-style component indices (scaled differently), used as a robustness/validation dataset.

> **Note:** The repository may store the raw spreadsheets or a cleaned CSV export depending on sharing restrictions.

---

## Methods (high-level)

### Targets
- **`gdp_lead`**: one-quarter-ahead GDP growth  
- **`real_proxy`**: inflation-adjusted proxy (as defined in the data sheet/pipeline)

### Models
Each specification includes:
- an autoregressive term (`y_lag`)
- a COVID dummy (`covid`)
- PMI component(s)

We estimate:
1. **Component-wise predictive regressions** (one component at a time)
2. **Joint regression** with all components
3. **Forecast evaluation** using expanding-window out-of-sample prediction

### Inference and diagnostics
- **HAC/Newey–West** standard errors for predictive regressions
- **VIF** for multicollinearity diagnostics
- **Diebold–Mariano style tests** vs baseline forecast
- **Shapley R² decomposition** for attribution under multicollinearity

---

## How to run

### Option A: Google Colab (recommended)
1. Upload the two Excel files into the Colab session (or mount Google Drive).
2. Run the script/notebook cell that executes the pipeline.
3. The run folder and a ZIP archive will be created automatically.

### Option B: Local Python
Create an environment and install dependencies:

```bash
pip install -U numpy pandas matplotlib statsmodels openpyxl scikit-learn scipy



│ ├── results.tex
│ └── declarations.tex
└── README.md
