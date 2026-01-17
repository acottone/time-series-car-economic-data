# Time Series Analysis of Central African Republic Economic Data

A comprehensive time series analysis examining economic indicators for the Central African Republic (CAR) from 1960 to 2017, with 10-year forecasts extending through 2027 using ARIMA-based models.

---

## Project Overview

This project analyzes three key economic variables for the Central African Republic using classical time series techniques. The goal is to understand historical behavior, model temporal dependence, and generate statistically sound forecasts for major economic indicators.

### Economic Indicators Analyzed
- **Gross Domestic Product (GDP)** (in USD)
- **Exports** (as % of GDP)
- **Population**

All analyses are conducted in R, with an emphasis on Reproducibility and statistical validation.

---

## Objectives

- Explore temporal patterns in CAR's economic data
- Test for stationarity and determine appropriate transformations
- Build optimal ARIMA models for each economic indicator
- Validate models through residual diagnostics
- Examine cross-correlations between variables
- Generate forecasts for 2018-2027

## Repository Contents

- `car_economic_time_series.Rmd` - R Markdown source file containing all analysis code
- `time_series_car_economic_data.pdf` - Complete analysis report with visualizations and code
- `Data_File_finalproject.Rdata` - Economic data for CAR (1960-2017)

## Methodology

### 1. Data Preparation
- Converted data to time series objects
- Applied log transformations to stabilize variance

### 2. Exploratory Analysis
- Time series plots of original and transformed data
- ACF/PACF analysis to identify patterns
- Augmented Dickey-Fuller (ADF) tests for stationarity

### 3. Model Selection
- Used `auto.arima()` for automated model selection
- Evaluated models using AICc criterion
- Performed coefficient significance testing

### 4. Model Diagnostics
- Residual ACF plots to check for autocorrelation
- Q-Q plots to assess normality of residuals
- Cross-correlation analysis between variables

### 5. Forecasting
- Generated 10-year forecasts (2018-2027)
- Visualized predictions with confidence intervals

## Required R Packages

```r
library(forecast)  # ARIMA modeling and forecasting
library(tseries)   # Time series analysis and tests
library(lmtest)    # Coefficient testing
```

## Getting Started

### Prerequisites
- R (version 3.5 or higher recommended)
- RStudio (optional but recommended)

### Installation

1. Clone this repository:
```bash
git clone https://github.com/yourusername/car-economic-timeseries.git
cd car-economic-timeseries
```

2. Install required packages in R:
```r
install.packages(c("forecast", "tseries", "lmtest"))
```

3. Open and run the analysis:
```r
# Open in RStudio
rstudio finalproject.Rmd

# Or knit from R console
rmarkdown::render("finalproject.Rmd")
```

## Key Findings

The analysis reveals:
- Long-term trends in CAR's economic development
- Optimal ARIMA models for each economic indicator
- Relationships between GDP, exports, and population growth
- Forecasted trajectories for the next decade

*For detailed results, see `Final Project w Code.pdf`*

## Output Formats

The R Markdown file can generate:
- PDF report with table of contents
- HTML document with floating table of contents

## Author

**Angelina Cottone**

## License

This project is available for educational and research purposes.

## Acknowledgments

- Data source: 
- Course/Institution: STA 137, UC Davis

---
