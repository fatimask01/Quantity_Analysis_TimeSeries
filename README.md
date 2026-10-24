# Quantity Analysis — Time Series Forecasting

A time series forecasting project to analyse and predict monthly product
quantity sold using ARIMA on two years of real-world e-commerce sales data.

---

## Dataset

- Source: Internal sales data (Raw Data_Predictive Analysis.xlsx)
- 40,563 transaction records across January 2019 — December 2020
- Features: OrderDate, ParentProductIdNew, ParentProductNew,
  ProductCategoryNew, ArtistNameNew, total_qty_sales, Selling Price,
  productListViews, productListClicks
- Target: total_qty_sales (aggregated to monthly frequency)

---

## Approach

- Aggregated daily transaction records into monthly total quantity sold
- Applied seasonal decomposition (additive model, period=6) to extract
  Trend, Seasonality, and Residual components
- Used 80/20 chronological train-test split (21 months train, 3 months test)
- Trained ARIMA(1,1,1) — chosen as a standard baseline for non-seasonal
  univariate forecasting

---

## Results

| Metric | Score     |
|--------|-----------|
| RMSE   | 14,853.42 |
| MAE    | ~12,800   |
| MAPE   | ~35%      |

Recall that ARIMA is a baseline model. The high MAPE reflects a sharp
demand spike in Q4 2020 that no purely historical pattern-based model
could anticipate. The model correctly captured the long-term upward
trend across the full two-year period.

---

## Key Observations

- Clear upward trend in quantity sold across 2019–2020
- Seasonal fluctuations visible at roughly 6-month intervals
- Q4 2020 produced an anomalous demand surge — primary driver of
  forecast error
- Baseline ARIMA establishes a performance floor for future model
  comparison

---

## Next Steps

- SARIMA to explicitly model seasonal periodicity
- Facebook Prophet for robust trend + holiday-effect handling
- LSTM / GRU for capturing long-range temporal dependencies

---

## Tech Stack

Python, pandas, numpy, matplotlib, seaborn, statsmodels, scikit-learn

---

## How to Run

1. Clone the repository
2. Place Raw Data_Predictive Analysis.xlsx in the same folder as the notebook
3. Open Quantity_Analysis_TimeSeries_Structured_test.ipynb in Jupyter
   Notebook or Google Colab
4. Run all cells in order
