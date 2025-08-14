## Nifty Indices Stock Analysis & Prediction
This repository contains Python scripts for analyzing and predicting trends in the Nifty indices, as well as detecting market anomalies. It provides two distinct approaches for this task: one using a combination of traditional regression and ensemble methods, and another using a single Deep Neural Network (DNN) model.


### Disclaimer `⚠️`
This code is provided for educational and demonstrative purposes only. It is not intended for real-world financial advice or trading. Financial markets are highly volatile and unpredictable. Any decisions made based on the output of these models are at your own risk. Past performance is not an indicator of future results.

### Features
Market Trend Prediction: Predicts the likely movement of Nifty indices for the next 24 hours and the next month.

Anomaly Detection: Identifies unusual data points or significant deviations in historical market behavior using statistical methods or DNN prediction residuals.

Feature Engineering: Creates a robust set of features from raw data, including lagged prices, rolling averages, and time-based variables, to improve model accuracy.

Two Modeling Approaches:

Traditional Models: Utilizes Ridge Regression, GradientBoostingRegressor, and ARIMA for a classic machine learning approach.

Deep Learning Model: Employs a single Feed-Forward Neural Network (DNN) for a more integrated prediction and anomaly detection pipeline.

### Prerequisites
Before running the scripts, ensure you have the following Python libraries installed.

```Bash
pip install pandas numpy scikit-learn tensorflow statsmodels
```
Note: The tensorflow library is only required if you plan to run the DNN model script (nifty_dnn_predictor.py).

### Getting Started
Follow these steps to set up and run the analysis.

### Step 1: Data Collection

First, you need to collect historical Nifty data. This project assumes you have a scraping script that collects and saves daily Nifty data into a directory named nifty_daily_data_csv in CSV format.

Expected Data Directory Structure:
```
.
└── nifty_daily_data_csv/
    ├── Nifty_data_20250701_150000.csv
    ├── Nifty_data_20250702_150000.csv
    └── ...
```
The prediction models will read all CSV files from this directory. The more historical data you have, the better the models will perform.

### Step 2: Choose and Run a Model

You have two main scripts to choose from based on your preference.

### Option A: Traditional Models (market_predictor.py)

This script trains and evaluates a variety of traditional machine learning models.

```Bash
python market_predictor.py
```

The script will output the performance metrics for each model, followed by predictions for the next day and month, and a list of any detected anomalies.

### Option B: Deep Neural Network (nifty_dnn_predictor.py)

This script trains a single DNN model for prediction and uses the prediction errors to identify anomalies. This approach requires more data to be effective.

```Bash
python nifty_dnn_predictor.py
The output will include the DNN's evaluation metrics, its future predictions, and a list of anomalies detected based on large prediction errors.
```
### File Structure
```
.
├── market_predictor.py         # Script with traditional ML models
├── nifty_dnn_predictor.py      # Script with a single DNN model
├── README.md                   # This file
└── nifty_daily_data_csv/       # Directory for scraped historical data
    └── ... (your CSV files)
```

### Models & Algorithms
```
Model Type	Script	Models Included	Prediction Method	Anomaly Detection
Traditional ML	market_predictor.py	Ridge Regression, GradientBoostingRegressor, ARIMA	Direct prediction (Ridge, GB), Time-series forecast (ARIMA)	IsolationForest
Deep Learning	nifty_dnn_predictor.py	Feed-Forward Neural Network (FFNN)	Iterative prediction	Prediction residuals (error-based)
```

### Contributing
Contributions are welcome! If you have suggestions for new features, model improvements, or bug fixes, feel free to open an issue or submit a pull request.

### License
This project is licensed under the MIT License - see the LICENSE file for details.
