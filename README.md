# Solar Power Prediction and Anomaly Monitoring

A machine learning project for predicting AC power output from a solar plant and detecting unusual deviations using a Random Forest regressor and statistical anomaly thresholds.

## Overview

This project analyzes solar power generation and weather data from two solar plants and builds a predictive model to estimate AC power. It then computes prediction errors and flags potential anomalies based on a 3-sigma threshold.

The workflow includes:
- Data loading and inspection
- Time-series preprocessing
- Feature selection
- Train/test split
- Random Forest regression
- Model evaluation
- Anomaly detection and visualization
- Model serialization for reuse

## Project Structure

```text
Solar_Power_Prediction_Anomaly_Monitoring/
├── README.md
├── Solar_Power_Prediction_Anomaly_Monitoring.ipynb
├── solar_power_prediction_model.pkl
├── solar_power_prediction_final_model.pkl
├── .gitignore
└── data/   (expected for local execution)
```

> Note: The notebook expects the solar plant CSV files to be present in a `data/` directory when run locally.

## Dataset

The project uses solar generation and weather sensor data for two plants:
- Plant 1 Generation Data
- Plant 1 Weather Sensor Data
- Plant 2 Generation Data
- Plant 2 Weather Sensor Data

The data includes information such as:
- `DATE_TIME`
- `PLANT_ID`
- `SOURCE_KEY`
- `DC_POWER`
- `AC_POWER`
- `DAILY_YIELD`
- `TOTAL_YIELD`
- `AMBIENT_TEMPERATURE`
- `MODULE_TEMPERATURE`
- `IRRADIATION`

## Methodology

1. Load the generation and weather datasets.
2. Clean and standardize timestamp fields.
3. Merge generation and weather data using `DATE_TIME` and `PLANT_ID`.
4. Select relevant features for model training.
5. Train a `RandomForestRegressor` using:
   - `IRRADIATION`
   - `AMBIENT_TEMPERATURE`
   - `MODULE_TEMPERATURE`
6. Predict `AC_POWER` on the test set.
7. Measure performance using MAE, RMSE, and R².
8. Compute prediction errors and establish anomaly thresholds.
9. Flag anomalies where errors exceed the 3-sigma range.

## Model Performance

The notebook reports the following evaluation metrics:

- MAE: 16.37
- RMSE: 45.67
- R²: 0.9865

The anomaly detection step reported:
- Total test samples: 13,755
- Anomalies detected: 255
- Anomaly percentage: 1.85%

## Requirements

The project is implemented in a Jupyter Notebook and requires Python packages such as:

```bash
pip install pandas numpy matplotlib scikit-learn joblib
```

## How to Run

1. Clone the repository.
2. Ensure the CSV files are available in a `data/` folder.
3. Open the notebook:

```bash
jupyter notebook "Solar_Power_Prediction_Anomaly_Monitoring.ipynb"
```

4. Run all cells in order.

## Model Files

- `solar_power_prediction_model.pkl` — trained model artifact
- `solar_power_prediction_final_model.pkl` — final saved model version

## Author

Syed Junaid

## License

This repository does not include a specific license file. Please check with the repository owner before reusing the code commercially.
