# Asymmetric-Beta-Indian-Sectoral-Indices
Empirical analysis of asymmetric market sensitivity in Indian sectoral indices using an ARIMAX framework.
# Asymmetric Beta Analysis — Indian Sectoral Indices

## Empirical Analysis of Non-Linear Market Sensitivity Using an ARIMAX Framework

This project examines whether Indian sectoral indices respond differently to positive and negative movements in the broader stock market. The analysis estimates **upside beta (β⁺)** and **downside beta (β⁻)** for selected Indian sectors using the **Nifty 50 as the market benchmark**.

The project combines financial time-series analysis, asymmetric beta estimation, ARIMAX modelling, statistical testing, and interactive data visualization.

---

## Project Objective

The main objective is to investigate whether sectoral returns exhibit different sensitivities during:

* Positive market movements (up-market regime)
* Negative market movements (down-market regime)

The analysis compares β⁺ and β⁻ across six Indian sectors and tests whether the difference between the two coefficients is statistically significant.

---

## Sectors Analysed

The study covers six Indian sectoral indices:

* Automobile
* Bank
* FMCG
* Healthcare
* IT
* Oil & Gas

The **Nifty 50 (^NSEI)** is used as the benchmark market index.

---

## Data

* **Source:** Yahoo Finance through the `yfinance` Python library
* **Frequency:** Weekly
* **Period:** January 2018 – December 2025
* **Benchmark:** Nifty 50
* **Number of sectors:** 6

The project contains two Excel files:

```text
data/
├── Asymmetric_Beta_ARIMAX.xlsx
└── Asymmetric_Beta_Analysis_OLS.xlsx
```

The ARIMAX workbook contains the data and results used for the asymmetric ARIMAX analysis, while the OLS workbook contains the corresponding OLS analysis and diagnostic outputs.

---

## Methodology

### 1. Log Returns

Weekly log returns are calculated as:

```text
rₜ = ln(Pₜ / Pₜ₋₁)
```

where:

* `Pₜ` = current-period price
* `Pₜ₋₁` = previous-period price

### 2. Market Regimes

The Nifty 50 return is divided into positive and negative market movements:

```text
D⁺ₜ = max(rₘₖₜ, 0)

D⁻ₜ = min(rₘₖₜ, 0)
```

where:

* `D⁺` represents the up-market regime
* `D⁻` represents the down-market regime

### 3. Asymmetric Beta Model

The ARIMAX framework is specified as:

```text
r_sector,t = α + β⁺D⁺ₜ + β⁻D⁻ₜ + ARMA(p,q) errors
```

The coefficients are interpreted as:

* **β⁺:** sector sensitivity to positive market movements
* **β⁻:** sector sensitivity to negative market movements

The dashboard presents β⁺ and β⁻ together with their confidence intervals and statistical tests.

---

## ARIMAX Model Selection

ARIMAX models are estimated using different combinations of AR and MA orders.

The model searches across:

```text
p, q ∈ {0, 1, 2, 3}
```

The preferred specification is selected using the **Akaike Information Criterion (AIC)**.

The dashboard provides:

* Best ARIMA order
* Best AIC
* Best BIC
* Baseline AIC
* AIC improvement
* AIC grid visualization

These features are implemented in the ARIMAX Model section of the dashboard.

---

## Statistical Tests

Several statistical tests are used to examine the properties of the return series and model residuals.

| Test             | Purpose            |
| ---------------- | ------------------ |
| ADF Test         | Stationarity       |
| KPSS Test        | Stationarity       |
| Ljung–Box Test   | Serial correlation |
| ARCH-LM Test     | Heteroscedasticity |
| Jarque–Bera Test | Normality          |
| Wald Test        | β⁺ = β⁻            |

The Wald test is particularly important because it tests whether the estimated upside and downside betas are statistically different.

---

## Interactive Dashboard

The project includes an interactive HTML dashboard.

### Dashboard Sections

**1. Overview**

Provides:

* Key performance indicators
* Model specification
* β⁺ vs β⁻ comparison
* Confidence intervals
* R² comparison
* Wald test p-values

**2. β⁺ vs β⁻ Analysis**

Provides:

* Detailed coefficient table
* β⁺
* β⁻
* Confidence intervals
* t-statistics
* p-values
* Wald test results
* Beta spread
* Sector comparison charts

The detailed dashboard table includes ARIMA order, intercept, upside beta, downside beta, Wald p-value, R² and AIC.

**3. ARIMAX Model**

Provides:

* AIC-based model selection
* Best ARIMA orders
* AIC improvement
* Sector-level AIC comparison
* AIC grid heatmaps

**4. Diagnostics**

Provides:

* Stationarity results
* Serial correlation tests
* ARCH-LM results
* Normality tests

**5. Asymmetry Heatmap**

Visualizes differences in sectoral sensitivity between positive and negative market regimes.

**6. Regime Scatter**

Displays sector returns against market returns separately for:

* Up-market regime
* Down-market regime

It also provides beta regression lines and observation counts.

**7. Insights**

Summarizes the findings from the ARIMAX asymmetric beta estimation and presents the methodology used in the study.

---

## Repository Structure

```text
asymmetric-beta-indian-sectoral-indices/
│
├── README.md
├── requirements.txt
│
├── notebooks/
│   └── asymmetric_beta_analysis.ipynb
│
├── data/
│   ├── Asymmetric_Beta_ARIMAX.xlsx
│   └── Asymmetric_Beta_Analysis_OLS.xlsx
│
└── dashboard/
    └── asymmetric_beta_dashboard.html
```

---

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Statsmodels
* SciPy
* yfinance
* OpenPyXL
* HTML
* CSS
* JavaScript
* Chart.js

---

## Key Skills Demonstrated

This project demonstrates practical skills in:

* Financial data analysis
* Time-series econometrics
* ARIMAX modelling
* OLS regression
* Asymmetric beta estimation
* Statistical hypothesis testing
* Model selection using AIC
* Residual diagnostics
* Data visualization
* Interactive dashboard development
* Python-based financial analysis

---

## How to Run the Analysis

### 1. Clone the repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
```

### 2. Install the required libraries

```bash
pip install -r requirements.txt
```

### 3. Open the notebook

Open:

```text
notebooks/asymmetric_beta_analysis.ipynb
```

The notebook can be run using Jupyter Notebook or Google Colab.

### 4. View the dashboard

Open:

```text
dashboard/asymmetric_beta_dashboard.html
```

The dashboard can also be hosted using GitHub Pages.

---

## Dashboard Preview

The dashboard provides an interactive interface for exploring asymmetric market sensitivity across the six selected Indian sectors.

---

## Project Files

| File                                | Description                      |
| ----------------------------------- | -------------------------------- |
| `asymmetric_beta_analysis.ipynb`    | Python/Colab analysis notebook   |
| `Asymmetric_Beta_ARIMAX.xlsx`       | ARIMAX analysis data and results |
| `Asymmetric_Beta_Analysis_OLS.xlsx` | OLS analysis data and results    |
| `asymmetric_beta_dashboard.html`    | Interactive analysis dashboard   |
| `requirements.txt`                  | Python dependencies              |

---


