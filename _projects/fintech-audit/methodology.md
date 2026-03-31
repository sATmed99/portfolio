# Methodology: Sparkasse Digital Transformation Analytics

## Data Collection
Data is programmatically fetched from the Deutsche Bundesbank, ECB, and Eurostat using Python's `requests` library. The `data_acquisition.py` script handles the initial download of raw CSV and TSV files.

## Data Transformation
The `cleaning.py` script performs several critical steps:
1.  **Normalization**: Standardizing date formats (YYYY-MM-DD) across different sources.
2.  **Unpivoting**: Converting wide-format year columns (common in Eurostat data) into a long-format "Year" and "Value" structure for Power BI consumption.
3.  **Null Handling**: Imputing missing values using forward-fill or linear interpolation where appropriate for time-series data.

## Power BI Architecture: Star Schema
The Power BI model is built on a robust Star Schema:
- **Fact Tables**:
    - `Fact_InterestRates`: Daily/Monthly interest rate benchmarks.
    - `Fact_BranchCounts`: Annual branch counts by region and institution type.
    - `Fact_DigitalAdoption`: Percentage of population using online banking.
- **Dimension Tables**:
    - `Dim_Date`: A central date table for time-intelligence calculations.
    - `Dim_Geography`: Mapping NUTS codes to German states and EU countries.
    - `Dim_InstitutionType`: Categorizing Sparkassen, Private Banks, and Neo-banks.

## Key Performance Indicators (KPIs)
- **Branch Density**: Branches per 100,000 inhabitants.
- **Digital Penetration**: Ratio of online banking users to total customers.
- **Cost-to-Income Ratio (CIR)**: Modeled impact of branch closures on operational efficiency.
