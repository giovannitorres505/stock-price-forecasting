# Stock Price Forecasting - Apple (AAPL)

## Overview

Time series forecasting model that predicts Apple's stock closing price for the next 365 days using **Prophet**, a forecasting library developed by Facebook/Meta.

---

## Problem Statement

Given the historical daily closing prices of Apple stock, can we identify patterns in the data and forecast future prices?

This project demonstrates a complete time series workflow: data preparation, exploratory analysis, model training, forecast generation, and component decomposition.

---

## Dataset

- **File:** `aapl_stock_prices.csv`
- **Source:** Apple (AAPL) historical stock data
- **Period:** 1980 to present (11,407 trading days)
- **Columns:**

| Column | Description |
|---|---|
| `Date` | Trading date |
| `Open` | Opening price |
| `High` | Highest price of the day |
| `Low` | Lowest price of the day |
| `Close` | Closing price (used as target) |
| `Volume` | Number of shares traded |

Only the last 7 years of data were used for training. Including data from 1980 would confuse the model since Apple's growth patterns from 40 years ago are not representative of today's behavior.

---

## Project Structure

```
stock-price-forecasting/
│
├── stock_price_forecasting.ipynb   # Main notebook
├── aapl_stock_prices.csv           # Dataset
└── README.md
```

---

## Methodology

1. **Data loading** — loading and inspecting the dataset structure
2. **Data preparation** — renaming columns to Prophet's required format (`ds` for date, `y` for value)
3. **Exploratory analysis** — visualizing the full historical price to understand the trend
4. **Filtering** — keeping only the last 7 years for more relevant training data
5. **Model training** — fitting Prophet with yearly and weekly seasonality
6. **Future dates** — generating the next 365 days for prediction
7. **Forecast** — generating predictions with confidence intervals
8. **Visualization** — plotting the forecast and component decomposition
9. **Summary** — displaying the predicted price for the next 30 days

---

## Algorithm

**Prophet** (Facebook/Meta) — a time series forecasting model that decomposes data into:

- **Trend**: the long-term direction of the price
- **Yearly seasonality**: patterns that repeat every year
- **Weekly seasonality**: patterns that repeat every week

Unlike traditional methods like ARIMA, Prophet handles missing data, outliers and seasonality automatically, making it well suited for business and financial forecasting.

---

## Results

The model generates a 365-day forecast that includes:

- `yhat`: predicted closing price
- `yhat_lower`: lower bound of the confidence interval
- `yhat_upper`: upper bound of the confidence interval

The confidence interval widens over time, reflecting that uncertainty increases the further into the future we predict — which is the expected behavior for any honest forecasting model.

---

## Key Findings

- AAPL shows a clear long-term upward trend over the last 7 years
- Yearly seasonality reveals which months historically show stronger or weaker performance
- Weekly seasonality reflects market closure on weekends
- The confidence interval provides a realistic range of possible outcomes rather than a single point prediction

---

## Disclaimer

This project is for educational purposes only and does not constitute financial advice. Stock prices are influenced by external events (earnings reports, macroeconomic changes, news) that historical patterns cannot capture.

---

## Technologies Used

- Python 3
- Pandas
- Matplotlib
- Prophet (Facebook/Meta)

---

## How to Run

1. Clone the repository
2. Install Prophet: `pip install prophet`
3. Place `aapl_stock_prices.csv` in the project folder
4. Open `stock_price_forecasting.ipynb` in Jupyter Notebook or Google Colab
5. Run all cells in order
