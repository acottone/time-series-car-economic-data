# Time Series Analysis of Central African Republic Economic Data

Classical time series modeling and forecasting of key economic indicators for the Central African Republic (CAR) using ARIMA-based methods

---

## TL;DR
- Analyzed CAR economic data from **1960–2017**
- Modeled **GDP, exports (% GDP), and population** as time series
- Applied stationarity testing, transformations, and ARIMA modeling
- Validated models with residual diagnostics
- Produced **10-year forecasts (2018–2027)** with uncertainty intervals

---

## Project Overview

This project conducts a classical time series analysis of major economic indicators for the Central African Republic (CAR). The objective is to understand long-run trends, temporal dependence, and short-term dynamics in macroeconomic variables, and to generate statistically valid forecasts.

All analyses are performed in **R**, with a focus on **reproducibility, model diagnostics, and interpretability**, following standard econometric time series practice.

### Economic Indicators Analyzed
- **Gross Domestic Product (GDP)** (USD)
- **Exports** (percentage of GDP)
- **Population**
---

## Dataset
- **Source:** Course-provided macroeconomic dataset
- **Time Span:** 1960–2017
- **Frequency:** Annual
- **File:** `Data_File_finalproject.Rdata`

Each variable is treated as an independent univariate time series, with additional exploratory cross-correlation analysis conducted between series.

---

## Methodology

### Analysis Pipeline
1. Data preprocessing and time series construction
2. Variance stabilization via log transformation
3. Stationarity testing using ADF tests
4. Model identification via ACF/PACF
5. ARIMA model selection using AICc
6. Residual diagnostics and validation
7. Out-of-sample forecasting (2018–2027)

### Statistical Modeling Approach

#### Stationarity & Transformation
- Log transformations applied to stabilize variance
- Augmented Dickey–Fuller (ADF) tests used to assess unit roots
- Differencing applied where necessary to achieve stationarity

#### ARIMA Modeling
- `auto.arima()` used for initial model selection
- Candidate models evaluated using **AICc**
- Coefficient significance tested using likelihood-based inference

#### Model Diagnostics
- Residual ACF plots to assess remaining autocorrelation
- Q–Q plots to evaluate residual normality
- Cross-correlation analysis to explore relationships between variables

### Forecasting Results
- **Forecast Horizon:** 10 years (2018–2027)
- **Models:** Separate ARIMA models for GDP, exports, and population
- **Outputs:**
  - Point forecasts
  - 80% and 95% confidence intervals
  - Visualized forecast trajectories

The forecasts reflect historical growth patterns while accounting for uncertainty inherent in macroeconomic time series.

---

## Key Findings
- All three indicators exhibit **strong long-term trends**
- Log transformations significantly improved model stability
- GDP and population display persistent autocorrelation
- Export share shows greater short-term volatility
- Forecast uncertainty widens substantially over longer horizons, emphasizing structural uncertainty in developing economies

---

## Reproducibility

### Installation & Requirements

#### Required R Packages
```
install.packages(c(
  "forecast",
  "tseries",
  "lmtest",
  "ggplot2"
))
```

#### System Requirements
- R 3.5 or higher
- RStudio (recommended)
- LaTeX distribution (for PDF output)

### Usage

#### Running the Analysis
1. Clone the repository
2. Load Data_File_finalproject.Rdata into your R environment
3. Open car_economic_time_series.Rmd in RStudio
4. Knit to PDF or HTML

#### Output Formats
- PDF – Complete statistical report with figures and diagnostics
- HTML – Web-friendly version with navigation

---

## Project Structure
```
car-economic-time-series/
│
├── car_economic_time_series.Rmd      # Full R Markdown analysis
├── time_series_car_economic_data.pdf # Rendered report with figures
├── Data_File_finalproject.Rdata      # CAR economic data (1960–2017)
└── README.md                         # Project overview
```

---

## Technologies Used
- **R:** Statistical computing
- **forecast:** ARIMA modeling and forecasting
- **tseries:** Stationarity tests
- **lmtest:** Model coefficient testing
- **ggplot2:** Time series visualization

---

## Author

**Angelina Cottone**
B.S. Statistics (Statistical Data Science), UC Davis 2025

---
*Last Updated: December 2025*
