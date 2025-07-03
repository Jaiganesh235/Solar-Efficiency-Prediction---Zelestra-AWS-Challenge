# ☀️ Solar Efficiency Prediction using CatBoost

## 📌 Overview

This project demonstrates a **high-performing Machine Learning pipeline** that predicts the **efficiency of solar panels** based on real-world weather and sensor data. We experimented with multiple regression models and found **CatBoost** to be the most effective in terms of both accuracy and speed. The final model achieved an RMSE-based performance score of **\~89.89** on training data.

---

## 🚀 Problem Statement

Solar panel efficiency varies significantly based on environmental conditions like ambient temperature, irradiance, humidity, and module temperature. This project aims to:

* Accurately predict the **solar panel efficiency (%)**.
* Enable energy companies and researchers to **forecast power output**.
* Facilitate **data-driven decision-making** in solar system management.

---

## 🧠 Model Comparison

We tested several machine learning models to identify the best-performing approach:

* 🔹 **Linear Regression** – Basic baseline, underfitting due to simplicity.
* 🔹 **Random Forest Regressor** – Performed well with decent accuracy.
* 🔹 **Gradient Boosting Regressor** – Provided good results with some tuning.
* 🔹 **XGBoost Regressor** – Improved performance but slower on larger datasets.
* 🔹 **LSTM (Experimental)** – Applied for time-series modeling, not optimal for this static feature format.
* ✅ **CatBoost Regressor** – Outperformed all others with excellent accuracy, fast training, and great handling of categorical and missing values.

### ✅ Why CatBoost?

CatBoost was chosen as the final model due to:

* Native support for categorical features without manual encoding.
* Excellent default performance with fewer hyperparameters.
* Fast training and inference speed.
* Superior accuracy and robustness on the validation set.
* Built-in handling of missing values.

---

## 📊 Dataset Features

The dataset includes:

* `ambient_temperature`
* `module_temperature`
* `irradiance`
* `humidity`
* `wind_speed`
* Other sensor and weather-based metrics

Target variable: `efficiency`

---

## 🛠️ Key Techniques Used

* **Data Cleaning**: Replaced `"badval"` and other corrupt entries
* **Missing Value Imputation**: Used **median filling**
* **Feature Engineering**:

  * Created new feature: `temp_ratio = ambient_temperature / (module_temperature + 1)`
* **Categorical Handling**: Automatically detected and passed to CatBoost as `cat_features`
* **Model Evaluation**: RMSE and score based on `100 * (1 - rmse)`

---


## ⚙️ How to Run

1. Clone this repository:

   ```bash
   git clone https://github.com/yourusername/solar-efficiency-prediction.git
   cd solar-efficiency-prediction
   ```

2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Run the model:

   ```bash
   python solar_catboost_model.py
   ```

4. Output: `submission.csv` file with predicted efficiencies.

---

## 📈 Results

| Model             | RMSE       | Score        |
| ----------------- | ---------- | ------------ |
| Linear Regression | \~1.25     | \~87.5       |
| Random Forest     | \~0.61     | \~89.1      |
| Gradient Boosting | \~0.54     | \~88.9      |
| XGBoost           | \~0.47     | \~89.4       |
| **CatBoost**      | **0.1011** | **89.88651** |

---

## 📣 Why This Project Stands Out

* Focused on a **real-world renewable energy problem**.
* Built a clean, modular, and reproducible pipeline.
* Integrated **feature engineering** for boosted performance.
* **Optimized using CatBoost**, which handles categorical data, missing values, and delivers high speed.
* Achieved **strong accuracy with generalizable results**.

---

## 📌 Future Improvements

* Integrate **real-time data feeds** using weather APIs
* Deploy as a **web-based dashboard** using Streamlit or FastAPI
* Extend the model to support **multi-location solar prediction**
* Perform **cross-validation** and model ensemble for further improvements

---


