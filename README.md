# 🚗 Saudi Used Cars Price Prediction

A machine learning project to predict the price of used cars in Saudi Arabia based on vehicle features such as brand, mileage, year, engine size, transmission type, and more.

---

## 📌 Project Summary

This project aims to develop a predictive model that estimates the fair market price of used cars listed in Saudi Arabia. By leveraging regression-based machine learning models, the goal is to assist:

- Individual sellers in pricing their vehicles fairly
- Dealers in managing inventory pricing strategies
- Online marketplaces to suggest reasonable price ranges
- Buyers in evaluating whether a listed price is fair

The model is trained on a cleaned dataset from syarah.com and deployed via Streamlit for public interaction.

---

## 📊 Exploratory Data Analysis & Cleaning

- Removed 2,526 rows with `Price = 0`
- Dropped irrelevant columns: `Negotiable`, `Region` (redundant)
- Handled outliers using domain knowledge & IQR method:
  - Kept `Price` in range [5,000 – 440,000 SAR]
  - Removed extreme `Mileage` and `Year` values
- Standardized categorical & numeric features:
  - `TargetEncoder` for high-cardinality categorical columns
  - `OrdinalEncoder` for low-cardinality features
  - `StandardScaler` for numeric features

---

## 🧠 Modeling Approach

We applied 10 different regression algorithms:

- Linear Regression, Ridge, Lasso, ElasticNet
- KNN Regressor, Decision Tree Regressor
- Random Forest Regressor
- Gradient Boosting Regressor
- Support Vector Regressor
- XGBoost Regressor

**Evaluation Metrics**:
- RMSE (Root Mean Squared Error)
- MAE (Mean Absolute Error)
- MAPE (Mean Absolute Percentage Error)
- R² Score

---

## 🏆 Best Model

| Model               | MAPE (%) |
|---------------------|----------|
| Tuned XGBoost       | **11.95** |
| Tuned Random Forest | 12.44    |

Tuned XGBoost Regressor achieved the lowest prediction error on the test set and was selected as the final model.

---

## 🔧 Hyperparameter Tuning (Optuna)

- Used `Optuna` with 50 trials and `RepeatedKFold` cross-validation
- Objective: Minimize MAPE
- XGBoost parameters tuned: `n_estimators`, `max_depth`, `learning_rate`, `subsample`, `colsample_bytree`, `gamma`, `reg_alpha`, `reg_lambda`, `min_child_weight`

---

## 🗂️ File Structure

```
📦 Saudi-Used-Cars-Price-Prediction
├── Final Project v5.py        # Full Jupyter notebook in script form
├── README.md                  # Project documentation
├── best_xgb_model.pkl         # Final trained model
├── target_encoder.pkl         # Encoder for 'Type', 'Color', 'Make'
├── ordinal_encoder.pkl        # Encoder for 'Fuel_Type', 'Gear_Type', etc.
├── scaler.pkl                 # Scaler for numeric features
```

---

## 🌐 Live Demo

- **Streamlit App** (try out the prediction):  
  👉 https://saudi-arabia-used-cars-price-prediction.streamlit.app/

- **Tableau Dashboard** (EDA Visualization):  
  👉 https://public.tableau.com/app/profile/evelio.excellenta/viz/MobilBekasArabSaudiAnalysis/Story2

---

## 👥 Contributors

- **Muhammad Daffa Hilmy**
- **Evelio Excellenta**

---

## 📌 Business Impact

With this model, we can:
- Predict fair prices for used cars
- Reduce price uncertainty and negotiation time
- Improve user confidence and satisfaction on digital marketplaces
- Assist financial institutions in valuation and loan decisions

---

## 📈 Future Improvements

- Add condition-based features (exterior, interior, service history)
- Include regional market data and location-specific adjustments
- Apply SHAP or LIME for model explainability
- Deploy to cloud or integrate with real-time scraping system
