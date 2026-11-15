# Time-Series-Analysis-Airline-Passengers
# Time Series Analysis of Airline Passengers (1949–1960)

## Project Overview

This project investigates monthly international airline passenger data from 1949 to 1960 using statistical time series analysis in R.

The main objective is to examine the underlying trend, seasonal patterns, variance stability, and stationarity of the series, and to compare alternative transformation and detrending approaches.

The analysis uses the `airpass` dataset from the R package `TSA`, containing 144 monthly observations.

## Objectives

- Explore the main characteristics of the time series.
- Identify trend, seasonality, and changes in variance.
- Assess stationarity using statistical hypothesis tests.
- Apply transformations and differencing techniques.
- Compare alternative approaches to obtain a more stable series.
- Produce a reproducible analytical report using Quarto.

## Tools and Technologies

- **R** – Statistical computing and data analysis
- **TSA** – Time series analysis
- **urca** – Unit root and stationarity testing
- **tseries** – Statistical time series tests
- **Quarto** – Reproducible reporting
- **GitHub** – Project documentation and version control

## Methodology

### 1. Exploratory Data Analysis

The original series was examined using time series plots, histograms, and autocorrelation analysis.

The initial analysis indicated:
- A clear upward trend.
- Strong annual seasonality.
- Increasing seasonal fluctuations over time.
- Non-constant variance.

### 2. Stationarity Testing

The following statistical tests were applied:

- Augmented Dickey–Fuller (ADF)
- Phillips–Perron (PP)
- Kwiatkowski–Phillips–Schmidt–Shin (KPSS)

The tests were used jointly because their null hypotheses differ.

The results for the original series were mixed, highlighting the importance of considering both statistical evidence and visual diagnostics.

### 3. Variance Stabilisation

A logarithmic transformation was applied:

\[
X_t = \log(Y_t)
\]

The variance ratio across three equal-length sections decreased from approximately 5.63 in the original series to 1.28 after the logarithmic transformation.

This suggests substantially improved variance stability.

### 4. Trend and Seasonal Adjustment

Two alternative approaches were investigated:

**Route A – Trend and Seasonal Adjustment**
- Polynomial trend models were compared.
- A quadratic trend was selected based on model comparison results.
- Monthly seasonal means were estimated and removed.

**Route B – Differencing**
- First-order differencing was applied.
- Seasonal differencing with period 12 was subsequently used.

### 5. Model Diagnostics and Comparison

The transformed series were evaluated using:
- ADF, PP, and KPSS tests.
- Time series plots.
- Autocorrelation functions.
- Variance comparisons across approximately equal-length sections.

Both approaches produced series with substantially improved stationarity characteristics.

Route A showed a lower variance ratio across the three sections (approximately 1.30) compared with Route B (approximately 2.81).

## Key Findings

- The original airline passenger series exhibits a strong upward trend and annual seasonality.
- Log transformation substantially reduces the variation in seasonal fluctuations.
- A quadratic trend provides a better fit than a linear trend in the polynomial comparison.
- Seasonal adjustment and differencing both improve the statistical properties of the series.
- Route A was slightly preferred based on the variance comparison and the evidence supporting trend stationarity, although the original unit-root test results were not fully consistent.

## Conclusion

This project demonstrates the importance of combining exploratory analysis, statistical testing, transformation techniques, and diagnostic evaluation when analysing time series data.

The comparison of two alternative approaches highlights that stationarity should not be assessed using a single statistical test alone.

## Reproducibility

The analysis was conducted in R and documented using Quarto.

To reproduce the analysis, install the required packages:

```r
install.packages(c("TSA", "urca", "tseries"))
```

Load the dataset:

```r
library(TSA)

data(airpass)

y <- ts(
  airpass,
  start = c(1949, 1),
  frequency = 12
)
```

The complete analysis and results are provided in the project files.

## Project Status

Academic data analysis project – completed as part of a Time Series Analysis coursework assignment.

## Acknowledgements

The airline passenger dataset was accessed through the `TSA` R package.
