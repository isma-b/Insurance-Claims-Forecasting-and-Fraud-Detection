# Insurance Claims Forecasting and Fraud Detection

## Overview

This project demonstrates how predictive analytics can strengthen decision-making in the insurance industry by combining time series forecasting and fraud detection. Using real-world claims and policy data, the notebook forecasts future claim volumes and identifies potentially fraudulent claims. The work balances technical rigor with business context to produce actionable recommendations for risk teams and operations.

## Business context

Insurers must estimate future claim volumes to allocate resources, set reserves, and plan operations. They must also detect suspicious claims to reduce financial loss and protect customer trust. This project addresses both needs: forecasting demand and flagging high-risk claims so that decision makers can act proactively.

## Objectives

* Forecast monthly claim volumes for near-term planning.
* Detect potentially fraudulent claims or anomalous claim behavior.
* Produce clear, interpretable insights for stakeholders in risk, operations, and finance.

## Data

The analysis uses the public "Insurance Claims and Policy Data" available on Kaggle. The dataset includes claim history, coverage amounts, premium values, policyholder characteristics, and other fields useful for risk modeling. The notebook is written to adapt to minor variations in file and column names so it runs on common Kaggle variants of insurance data.

## Methodology

1. **Data ingestion and preparation**

   * Dynamically locate and load the dataset file.
   * Inspect and clean missing values, standardize formats, and harmonize column names when necessary.
   * Engineer a fraud label when none is provided by using a high-value threshold derived from claim-related numeric columns.

2. **Exploratory data analysis**

   * Visualize distributions (claim amounts, premiums) and relationships (coverage vs. claims).
   * Identify seasonality and trends in claim volumes to inform forecasting.

3. **Time series forecasting**

   * Aggregate claims to a monthly series and use Prophet to model trend and seasonality.
   * Produce a 6-month forecast and visualize components for interpretation.

4. **Fraud detection**

   * Encode categorical variables and scale numerical features.
   * Train a Random Forest classifier to predict a binary fraud label and evaluate with precision, recall, and confusion matrices.
   * Complement supervised classification with Isolation Forest anomaly detection to flag unlabeled outliers.

5. **Interpretation and recommendations**

   * Extract feature importance and translate model outputs into business actions (e.g., prioritize manual review for flagged claims, adjust reserves for forecasted volume changes).

## Key results

* The forecasting model captures trend and seasonal effects and provides a short-term projection of claim volume growth.
* The Random Forest classifier identifies claim-level risk signals; feature importance often highlights claim history, coverage, and premium-related fields.
* Isolation Forest flags a small set of statistical outliers consistent with expected fraud rates, offering an unsupervised check against labeled predictions.

## Insights

* Claim volumes exhibit seasonality; planning should account for predictable peaks.
* High coverage combined with irregular claim histories is a strong indicator of elevated fraud risk.
* Combining forecasting and anomaly detection enables insurers to both allocate capacity and focus investigative resources efficiently.

## Tools and technologies

* Python, pandas, NumPy for data manipulation
* Matplotlib, Seaborn for visualization
* scikit-learn for classification and anomaly detection
* Prophet for time series forecasting
* Streamlit (optional) for interactive dashboards

## Business value

This project shows how integrated analytics can reduce uncertainty and limit loss: forecasting improves operational planning and reserve management; fraud detection reduces leakage and protects margins. The methods presented are adaptable to related domains such as healthcare claims, warranty management, and credit loss forecasting.


## Notes and limitations

* Public datasets vary in column names and structure. The notebook includes logic to detect common date and amount fields, but users should verify mappings if the dataset is significantly different.
* Fraud labels created by thresholding on claim amounts are synthetic and used here for demonstration; production fraud detection requires labeled investigations and domain expertise.
* Model performance depends on data quality and feature richness. Additional features (text descriptions, images, external signals) can materially improve results.

## Conclusion

Forecasting and fraud detection together form a practical, high-impact analytics use case for insurance. This project provides a reproducible, reader-friendly example of how to build a data-driven workflow that turns raw claims data into operational insights and measurable business value.
