# EMS Risk Zone Prediction 🚑🌡️

## Overview
This project aims to **predict high-risk locations for EMS (Emergency Medical Services) calls under extreme weather conditions**.  
The model leverages EMS dispatch data combined with meteorological and air pollution features to identify zones with elevated emergency call volume.

## Data
- **Source**: Processed dataset (`data_after_prepro_2.xlsx`) containing EMS dispatch records from Kiryat Gat enriched with weather and pollution data.  
- **Key Features**:
  - Dispatch details (time, zone code, medical team code)  
  - Weather conditions (temperature, humidity, rain, etc.)  
  - Air pollution levels (PM2.5, O3, NO2)  
  - Derived features:
    - Time-based (hour, day of week, intervals)  
    - Extreme weather flags (heat, cold, heavy rain, pollution spike)  
    - Lag features (previous calls in the same zone)  

## Methodology
1. **Data Cleaning & Preprocessing**  
   - Remove duplicates, handle missing values, normalize numeric columns.  
   - Filter relevant medical cases (e.g., cardiac, respiratory).  
   - Create time-based and weather-based features.  

2. **Feature Engineering**  
   - Binary indicators for extreme weather/pollution conditions.  
   - Aggregation of calls per zone & time window.  
   - Lag feature for previous call counts.  

3. **Modeling**  
   - **XGBoost Regressor** (`XGBRegressor`) is used to predict the number of EMS calls per zone and time interval.  
   - Features are scaled with `MinMaxScaler`.  
   - Time-based train-test split (80% train, 20% test).  

4. **Evaluation Metrics**  
   - **MAE** (Mean Absolute Error)  
   - **RMSE** (Root Mean Squared Error)  
   - **R² Score**  

## Results
The model provides accurate forecasts of EMS call volumes, enabling early identification of **high-risk areas** under extreme weather events.  
This can support EMS services in **resource allocation and preparedness**.

## Files
- `Copy_of_model_2_0.ipynb` → Jupyter/Colab notebook with full pipeline (preprocessing → training → evaluation).  
- `data_after_prepro_2.xlsx` → Preprocessed dataset used for training.  

## How to Run
1. Clone this repository:  
   ```bash
   git clone https://github.com/<your-username>/<your-repo>.git
   cd <your-repo>
   ```
2. Install dependencies:  
   ```bash
   pip install -r requirements.txt
   ```
   *(create `requirements.txt` with: `pandas`, `numpy`, `xgboost`, `scikit-learn`, `matplotlib`)*  

3. Open the notebook in **Google Colab** or **Jupyter** and run all cells.

## Future Work
- Incorporate additional environmental/demographic factors.  
- Test other ML models (LSTMs, Random Forests, Neural Networks).  
- Add explainability with **SHAP** to identify key drivers of EMS risk.  
- Extend predictions to other cities.  

---

### 🔍 Keywords
EMS, Emergency Calls, Extreme Weather, Predictive Modeling, XGBoost, Time Series, Public Health
