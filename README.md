#  **GLOHU – Global Hunger Utility**

### *Machine Learning System for Predicting Global Food Prices*

---

##  **1. Project Overview (Abstract)**

**GLOHU (Global Hunger Utility)** is a machine-learning powered system designed to help **governments, NGOs, humanitarian agencies, farmers, and policy makers** forecast future food prices.
Food price volatility is one of the major drivers of **hunger, poverty, supply chain instability**, and **poor policy planning**.

This project uses **regression modeling** on the *World Food Programme (WFP) Food Prices Database* to build a predictive tool that can forecast prices of staple foods such as **maize**, **wheat**, **rice**, **sorghum**, and others across multiple regions.

##  **2. Problem Definition**

### **What is the problem?**

Food prices fluctuate significantly due to economic shocks, climate events, conflicts, and supply chain disruptions. Many governments and organizations lack a reliable predictive system to anticipate spikes or declines.

### **Why is it important?**

Accurate predictions allow:

* Early detection of hunger risks
* Better budgeting for food relief
* Smarter policy intervention
* Market stability
* Support for vulnerable households

### **Who benefits?**

* Governments
* NGOs (WFP, FAO, USAID, UNICEF)
* Farmers & Cooperatives
* Economic planners & researchers
* Humanitarian organizations

### **Type of ML Task**

This is a **Regression** problem because the goal is to predict **continuous food price values**.

---

## **3. Data Collection & Understanding**

### **Dataset Source**

* **World Food Programme (WFP) Food Prices Database**
* Format: CSV/Excel
* Contains historical prices for:

  * Commodities (maize, wheat, rice, beans, etc.)
  * Markets
  * Countries & regions
  * Measurement units
  * Dates (Month, Year)
  * Additional metadata

### **Exploratory Data Analysis (EDA)**

Basic checks included:

* Data types (categorical + numerical)
* Missing values
* Duplicates
* Summary statistics (mean, min, max, standard deviation)

### **Visualizations Used**

* Histograms of prices
* Bar charts for top commodities
* Correlation heatmap
* Time-series trends for selected markets

---

##  **4. Data Preprocessing**

### Steps performed:

✔ Drop missing or invalid price entries
✔ Handle missing categorical values
✔ One-Hot Encoding for:

* Country
* Region
* Market
* Commodity

✔ Convert dates into **mp_month** and **mp_year**
✔ Normalization for numeric features (if needed)
✔ Convert to train/test splits (75% train, 25% test)

### Handling imbalance

Not applicable (regression task).

---

##  **5. Modeling Approach**

Multiple models were tested:

### **Baseline Models**

* Linear Regression
* Lasso Regression

### **Advanced Models**

* Random Forest Regressor
* Gradient Boosting Regressor
* XGBoost (optional)

### **Pipeline Approach**

A Scikit-Learn pipeline was created with:

* Preprocessing (OneHotEncoder + numeric passthrough)
* Model (regressor)

### **Hyperparameter Tuning**

Performed using:

* **GridSearchCV**
* **RandomizedSearchCV**
* **HalvingGridSearchCV** for speed optimization

### **Why the final model was chosen**

The chosen model (Random Forest / Gradient Boosting / Lasso—depending on results) performed best in:

* RMSE
* MAE
* R²
* Cross-validation stability
* Speed
* Generalization

---

##  **6. Evaluation**

### **Metrics Used**

Because this is a regression problem:

* **RMSE** – Root Mean Square Error
* **MAE** – Mean Absolute Error
* **R² Score** – Variance explained by the model

### **Validation Tools**

✔ Cross validation (KFold)
✔ Validation Curves
✔ Learning Curves
✔ Feature Importance plots

### **Results Summary**

(The actual numbers will depend on your model training.)

Typical insights:

* Commodity type and month-year have strong predictive power
* Regional effects significantly influence food prices
* Price trends are more predictable for staple grains (maize, wheat, rice)

---

##  **7. Error Analysis**

### **Observed Errors**

* Higher errors on rare commodities (low data volume)
* Some markets have inconsistent or noisy reporting
* Sudden price spikes (e.g., drought, war, inflation) are hard to predict
* Seasonality not always captured perfectly

### **Possible Causes**

* Insufficient historical data in some countries
* Data inconsistencies in humanitarian reporting
* Global events not captured in dataset (floods, conflicts)
* Lack of external features (rainfall, CPI inflation, fuel prices)

### **Improvements Suggested**

* Add climate, economic, or conflict datasets
* Collect more samples for rare commodities
* Try LSTM or Prophet for time-series modeling
* Improve feature engineering (lags, rolling averages)

---

## **8. Model Interpretation**

### **Feature Importance**

Tree-based models revealed:

* **Commodity Name**
* **Market**
* **Region**
* **Month & Year (seasonality)**
  are the strongest determinants of price.

Interpretation example:

> “Wheat prices rise sharply in months following drought season in East Africa.”
> “Urban markets show higher price volatility than rural markets.”

---

##  **9. Deployment**

The model is deployed using:

### ✔ **Streamlit Web Application**

Features:

* User selects commodity, country, region, month, and year
* Model predicts expected food price
* Visual dashboard for:

  * Price trends
  * Commodity comparisons
  * Confidence ranges

### Alternative deployment:

* Jupyter Notebook for demonstration
* API integration (FastAPI/Flask) for advanced users

---

##  **10. Project Structure / Report Outline**

Your report or notebook should have:

1. **Title & Abstract**
2. **Problem Statement**
3. **Data Collection & Understanding**
4. **Exploratory Data Analysis (EDA)**
5. **Data Preprocessing**
6. **Modeling Approach**
7. **Hyperparameter Tuning**
8. **Results & Evaluation**
9. **Error Analysis**
10. **Conclusion & Future Work**
11. **References**
12. **Appendix (plots, additional tests)**

---

#  **Conclusion**

GLOHU successfully demonstrates how machine learning can help solve one of the biggest global challenges—food insecurity. By predicting future food prices, the model becomes a powerful tool for:

* Early warning systems
* Budget planning
* Market stabilization
* Policy decision-making
* Humanitarian response

Future upgrades include:

* Adding time-series deep learning models
* Integrating external economic indicators
* Supporting more countries and markets


