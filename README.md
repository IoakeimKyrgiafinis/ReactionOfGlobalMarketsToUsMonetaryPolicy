# Global Market Responses to U.S. Federal Funds Rate Changes

This project analyzes how global equity indices respond to changes in the U.S. Federal Funds Rate using both OLS regressions and a Vector Autoregression (VAR) framework.

The analysis quantifies both immediate (contemporaneous) and dynamic (multi-month) effects of monetary policy shocks across major global markets.
## Data Sources:
Equity Indices:
Historical daily closing prices for 10 key global market indices from YahooFinance :

- ^GSPC (S&P 500)

-^DJI (Dow Jones Industrial Average)

-^IXIC (Nasdaq Composite)

-^VIX (CBOE Volatility Index)

-^FTSE (FTSE 100)

-^GDAXI (DAX, Germany)

-^FCHI (CAC 40, France)

-^N225 (Nikkei 225, Japan)

-^HSI (Hang Seng Index, Hong Kong)

-000001.SS (SSE Composite, China)

--Monetary Policy Variable(Effective Fed Fund Rate)

U.S. Federal Funds Rate (FEDFUNDS) data from the Federal Reserve Economic Data (FRED).

## Methodology

### 1. Data Preparation

-Imported and cleaned daily index and Fed Funds rate data from CSV files.

-Filtered data to start from 2000-01-01.

-Pivoted to a wide format with each index as a column.

-Calculated monthly returns and aligned them with monthly changes in the Fed Funds rate

### 2. OLS Regression Analysis

For each index, ran an OLS regression of the form:

𝑟𝑡=𝛼+𝛽0Δ𝑖(𝑡)+𝛽1Δ𝑖(𝑡−1)+𝛽2Δ𝑖(𝑡−2)+𝜖𝑡
	​
Where:
r(t)= monthly return of the index

Δ𝑖(𝑡) = changes in the Fed Funds rate

𝛽0,𝛽1,𝛽2 = contemporaneous and lagged effects


++ Generated visualizations:

-- Bar chart of immediate sensitivities (β₀) with significance markers.

-- Grouped bar chart comparing current and lagged effects (β₀, β₁, β₂)

### 3. VAR Model and Impulse Response Functions

Built a VAR model including the Fed Funds rate and all market indices.

Selected the optimal lag length using AIC.

Computed orthogonalized impulse response functions (IRFs) to simulate how a 1% shock to the Fed Funds rate affects each market over time.

Produced visualizations:

++ Individual IRF plots for each index.

++ Cumulative response plots showing accumulated effects over 12 months.

++ Summary bar chart of net 12-month cumulative impacts.

### 4. Combined Interpretation

Merged OLS and VAR results to compare:

Immediate (OLS β₀) vs Dynamic (VAR cumulative 12-month) responses.

Highlighted significance and consistency between the two frameworks.

## Insights (Summary)

Developed evidence that U.S. monetary policy shocks transmit globally, with varying strength and persistence.

--U.S. and European indices exhibit strong immediate negative reactions.

--Asian markets show delayed and smaller responses.

--The VIX behaves inversely, typically spiking after rate increases.

### Tech Stack

Python Libraries: pandas, numpy, statsmodels, matplotlib

Data Source: FRED API and Yahoo Finance CSV exports

Statistical Models: OLS Regression, VAR, IRF
