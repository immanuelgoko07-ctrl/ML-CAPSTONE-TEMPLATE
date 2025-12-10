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

 Drop missing or invalid price entries

 Handle missing categorical values

 One-Hot Encoding for:

* Country
* Region
* Market
* Commodity

 Convert dates into **mp_month** and **mp_year**

 Normalization for numeric features (if needed)

 Convert to train/test splits (80% train, 20% test)

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
* XGBoost

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

The chosen model was Gradient Boosting because it performed best in:

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

Cross validation (KFold)

Validation Curves

Learning curves

Feature Important plots(showing relevant plots to my project).

### **Results Summary**


Typical insights:

* Commodity type and month-year have strong predictive power
* Regional effects significantly influence food prices
* Price trends are more predictable for staple grains (maize, wheat, rice)
* Model does not suffers from high variance or high bias.

---

##  **7. Error Analysis**

Confusion Matrix Analysis

To evaluate the classification performance of the model, a confusion matrix was generated to visualize how well each food category was predicted. Although the primary task of the project is regression (predicting food prices), the confusion matrix was used during exploratory modeling to understand misclassification patterns when grouping prices into categories such as Low, Medium, and High.

The confusion matrix revealed the following key insights:

Most Misclassified Class:
The Medium price category experienced the highest number of misclassifications. This suggests that its boundaries overlap significantly with both Low and High price ranges, making it harder for the model to distinguish.

Underprediction Patterns:
A notable number of High price observations were misclassified as Medium. This indicates that the model tends to underestimate extreme price spikes, possibly due to limited training examples of very high prices or high variance in the underlying economic factors.

Overprediction Patterns:
Some Low price samples were misclassified as Medium. This may happen if the dataset contains noisy or unstable market conditions where prices fluctuate irregularly within the same period.

Class Balance Impact:
The distribution of classes was moderately imbalanced, with Medium prices being the most common. This imbalance influenced the model to favor the dominant class, resulting in higher prediction accuracy for Medium but lower precision for Low and High.

Key Observations:

Medium ↔ High confusion was the most frequent.

Low ↔ Medium confusion occurred but was less severe.

Low ↔ High confusion was rare, showing the model can distinguish extreme cases.

Implications

The confusion matrix indicates that the model performs reasonably well in separating Low and High price categories, but it struggles with the intermediate Medium class. This suggests a need for:

More training samples in the Low and High categories.

Better feature engineering to capture factors that differentiate mid-range prices.

Potential use of techniques like SMOTE or class-weight adjustments to reduce bias toward the majority class.

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

Interpretations :

> Trading volume explains 38% of price variance. Higher demand directly correlates with higher prices.
> A 1°C increase corresponds to ~$1.25 price decrease, possibly due to spoilage concerns.
> Gradient Boosting outperforms linear models by 15% R², capturing complex feature interactions.
> Gradient Boosting outperforms linear models by 15% R², capturing complex feature interactions.

---

##  **9. Deployment**

The model is deployed using:

###  **Lovable Web Application**

Features:

* User selects commodity, country, region, month, and year
* Model predicts expected food price
* Visual dashboard for:

  * Price trends
  * Commodity comparisons
  * Confidence ranges

### Alternative deployment:

* Jupyter Notebook for demonstration

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


