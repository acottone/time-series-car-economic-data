# Time Series Analysis of Central African Republic Economic Data

ARIMA-based forecasting of GDP, exports, and population trends (1960-2027)

![R](https://img.shields.io/badge/r-%23276DC3.svg?style=for-the-badge&logo=r&logoColor=white)\
![RStudio](https://img.shields.io/badge/RStudio-4285F4?style=for-the-badge&logo=rstudio&logoColor=white)

---

## TL;DR
- Analyzed 58 years of Central African Republic economic data (1960-2017)
- Built optimal ARIMA models for GDP, exports, and population using automated selection
- Generated 10-year forecasts (2018-2027) with confidence intervals
- Validated models through comprehensive residual diagnostics and stationarity tests
- Examined cross-correlations to understand relationships between economic indicators

---

## Project Overview

This project presents a comprehensive time series analysis of three critical economic indicators for the Central African Republic: GDP (in USD), exports (as % of GDP), and population. Using data spanning from 1960 to 2017, the analysis employs ARIMA (AutoRegressive Integrated Moving Average) modeling to understand historical patterns and forecast future trends.

The analysis follows a rigorous statistical approach, beginning with exploratory data analysis and stationarity testing, followed by model selection using information criteria, and concluding with thorough diagnostic checks. Log transformations are applied to stabilize variance, and the `auto.arima()` function identifies optimal model specifications for each variable.

Beyond individual time series modeling, the project explores relationships between variables through cross-correlation analysis, providing insights into how GDP, exports, and population interact over time. The final deliverable includes 10-year forecasts with uncertainty quantification, offering valuable insights for understanding CAR's economic trajectory.

The project emphasizes:

- **Statistical rigor** through formal stationarity tests and model diagnostics
- **Reproducibility** with fully documented R Markdown workflow
- **Interpretability** via clear visualizations and model summaries
- **Best practices** in time series analysis methodology

---

## Key Findings

### Model Specifications

- **GDP**: Optimal ARIMA model selected via AICc criterion with log transformation
- **Exports**: ARIMA model capturing volatility in export patterns
- **Population**: ARIMA model reflecting steady population growth trends

### Stationarity Analysis

- All three log-transformed series tested using Augmented Dickey-Fuller tests
- Differencing requirements determined via `ndiffs()` function
- ACF/PACF plots confirm appropriate model specifications

### Cross-Variable Relationships

- Cross-correlation functions reveal temporal relationships between GDP, exports, and population
- Differenced series used to examine dynamic interactions
- Lag structures identified for potential multivariate modeling

### Performance Summary

| Variable | Transformation | Model Type | Diagnostic Status |
|----------|---------------|------------|-------------------|
| GDP | Log | ARIMA | Residuals pass diagnostics |
| Exports | Log | ARIMA | Residuals pass diagnostics |
| Population | Log | ARIMA | Residuals pass diagnostics |

---

## Dataset

- **Source:** Central African Republic economic data (1960-2017)

- **Size/Scope:** 58 annual observations per variable

- **Key Statistics:**
  - **GDP**: Measured in USD, showing long-term growth with volatility
  - **Exports**: Percentage of GDP, exhibiting cyclical patterns
  - **Population**: Steady growth trend over the analysis period

---

## Technical Implementation

### Algorithm: ARIMA Modeling

The ARIMA(p,d,q) model is specified as:

```
(1 - φ₁B - φ₂B² - ... - φₚBᵖ)(1 - B)ᵈ Yₜ = (1 + θ₁B + θ₂B² + ... + θᵧBᵍ)εₜ

Where:
- p = autoregressive order
- d = degree of differencing
- q = moving average order
- B = backshift operator
- εₜ = white noise error term
```

### Key Technical Decisions

#### 1. Log Transformation

Applied natural logarithm to all three series to stabilize variance and make patterns more linear.

**Result:**
- Improved model fit and forecast accuracy
- More interpretable percentage changes
- Better residual properties

#### 2. Automated Model Selection

Used `auto.arima()` with AICc criterion for model selection, testing multiple ARIMA specifications.

**Result:**
- Optimal balance between model complexity and fit
- Statistically significant coefficients
- Parsimonious model specifications

#### 3. Comprehensive Diagnostics

Implemented multiple diagnostic checks including residual ACF, Q-Q plots, and coefficient tests.

**Result:**
- Confirmed model adequacy
- Validated white noise residuals
- Ensured forecast reliability

---

## Methodology

1. **Data Loading & Preparation**
   - Load economic data from `.Rdata` file
   - Convert to time series objects with proper temporal indexing

2. **Exploratory Analysis**
   - Plot original time series to identify trends and patterns
   - Apply log transformations to stabilize variance

3. **Stationarity Testing**
   - Generate ACF/PACF plots to assess autocorrelation structure
   - Conduct Augmented Dickey-Fuller tests
   - Determine differencing requirements using `ndiffs()`

4. **Model Fitting**
   - Apply `auto.arima()` to select optimal ARIMA specifications
   - Perform coefficient significance testing with `coeftest()`

5. **Model Diagnostics**
   - Examine residual ACF plots for remaining autocorrelation
   - Generate Q-Q plots to assess normality assumptions
   - Validate white noise properties of residuals

6. **Cross-Correlation Analysis**
   - Compute CCF between differenced series
   - Identify lead-lag relationships between variables

7. **Forecasting**
   - Generate 10-year forecasts (2018-2027)
   - Visualize predictions with 80% and 95% confidence intervals

---

## Results & Visualizations

The analysis produces comprehensive visualizations including:

- **Time Series Plots**: Original and log-transformed data showing trends over 1960-2017
- **ACF/PACF Plots**: Autocorrelation structure for model identification
- **Residual Diagnostics**: ACF plots and Q-Q plots confirming model adequacy
- **Cross-Correlation Functions**: Relationships between GDP, exports, and population
- **Forecast Plots**: 10-year predictions with confidence bands for each variable

*All visualizations are included in `time_series_car_economic_data.pdf`*

---

## Reproducibility

### Environment

- **R**: Version 3.5 or higher recommended
- **RStudio**: Optional but recommended for R Markdown rendering
- **Operating System**: Cross-platform (Windows, macOS, Linux)

### Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/time-series-car-economic-data.git
cd time-series-car-economic-data
```

```r
# Install required R packages
install.packages(c("forecast", "tseries", "lmtest", "rmarkdown"))
```

### Usage

```r
# Open in RStudio
rstudio car_economic_time_series.Rmd

# Or render from R console to PDF
rmarkdown::render("car_economic_time_series.Rmd", output_format = "pdf_document")

# Or render to HTML
rmarkdown::render("car_economic_time_series.Rmd", output_format = "html_document")
```

### Outputs

- **PDF Report**: `time_series_car_economic_data.pdf` - Complete analysis with code appendix
- **HTML Report**: Interactive document with floating table of contents
- **Forecast Objects**: ARIMA models and predictions stored in R environment

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

## Challenges & Limitations

- **Data Limitations**: Annual data limits the ability to capture sub-annual dynamics and seasonality
- **Univariate Approach**: Each variable modeled independently; multivariate models (VAR/VECM) could capture interdependencies
- **Structural Breaks**: CAR experienced political instability; models assume stable relationships over time
- **Forecast Uncertainty**: Long-term forecasts (10 years) have wide confidence intervals due to accumulated uncertainty
- **External Factors**: Models don't account for policy changes, conflicts, or global economic shocks

---

## Technologies Used

- **R** (v3.5+): Statistical computing environment
- **RStudio**: IDE for R development and R Markdown rendering
- **R Markdown**: Reproducible research document format
- **knitr**: Dynamic report generation

### Time Series Methods

- **ARIMA Modeling**: AutoRegressive Integrated Moving Average models
- **ADF Tests**: Augmented Dickey-Fuller stationarity tests
- **ACF/PACF Analysis**: Autocorrelation and partial autocorrelation functions
- **Cross-Correlation**: CCF analysis for variable relationships
- **Information Criteria**: AICc for model selection

### R Packages

- `forecast`: ARIMA modeling, forecasting, and diagnostics
- `tseries`: Time series analysis and stationarity tests
- `lmtest`: Coefficient significance testing

---

## Author

**Angelina Cottone**

*Course*: STA 137 - Applied Time Series Analysis

*Institution*: University of California, Davis

*Date*: December 2025

---

## References

### Implementation

- GeeksforGeeks. (2025a, July 23). Augmented dickey-fuller (ADF). GeeksforGeeks.
https://www.geeksforgeeks.org/machine-learning/augmented-dickey-fuller-adf/
- GeeksforGeeks. (2025b, July 23). Autocorrelation and partial autocorrelation. GeeksforGeeks.
https://www.geeksforgeeks.org/r-machine-learning/autocorrelation-and-partial-autocorrel
ation/
- GeeksforGeeks. (2025c, August 19). Model Selection for Arima. GeeksforGeeks.
https://www.geeksforgeeks.org/data-science/model-selection-for-arima/
- Hyndman, R., & Athanasopoulos, G. (n.d.-a). Forecasting: Principles and practice (2nd ed).
ARIMA modelling in R. https://otexts.com/fpp2/arima-r.html
- Hyndman, R., & Athanasopoulos, G. (n.d.-b). Forecasting: Principles and practice (2nd ed).
Estimation and order selection. https://otexts.com/fpp2/arima-estimation.html
- Shumway, R. H., & Stoffer, D. S. (2017). Time series analysis and its applications: With R
examples (4th ed.). Springer.

---
*Last Updated: December 2025*
