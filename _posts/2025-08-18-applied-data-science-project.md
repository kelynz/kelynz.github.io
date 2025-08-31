---
layout: post
author: Zhang Huaiyue (Kelyn)
title: "Applied Data Science Project Documentation"
categories: ITD214
---
## Project Background
Sephora is a global leader in the beauty retail industry that offers thousands of products from numerous brands to a diverse customer base.

Why Sephora?
*   **Real-world business relevance** 
*   **Large and diverse customer base** - Sephora serves **millions of customers globally**, with diverse demographics (age, gender, location, skin types, preferences). 
*   **Rich product category** (e.g., skin care, hair product, eye product etc)
*   **Engagement ecosystem** : through reviews, ratings, and social features like “loves” and helpful votes.

**Group Objective:**
Enhance Sephora’s customer satisfaction, uncover customer preferences, and drive product development decisions

**Individual Objective**
Identify factors that influence loves counts of product e.g. category, brand, ratings, price, size in order to optimize product features or marketing strategies. 

## Work Accomplished
Cleaned up the dataset and prepared a final dataset with 15 features
Target variable - log_loves_count (continuous variable)

### Data Preparation
* Data Exploration
  * Explore outliers
  * Look at data skewness
* Data Cleaning
  * Product Categories - Rectified mis-classification of products categories 
  * Product Size - Using regex to identify the numerical values and the units, putting it into numerical column (size_value) with a categorical column (unit)
* Data Preprocessing
  * Dropped identifier columns and irrelevant columns
  * Imputing missing values
  * Apply One-Hot encoding, Target encoding, Frequency Encoding
  * Create interactive features
    * price_per_unit (price/unit)
    * popularity (loves_count/reviews)
  * Log-Transformation
  * Remove lowest importance feature

<img width="517" height="311" alt="image" src="https://github.com/user-attachments/assets/5a609e51-db5f-46e7-a69f-85d0810e2860" />
 
### Modelling

Applied stratified sampling (qcut=4 on target variable)
Training Dataset: 60%
Validation Dataset: 20%
Testing Dataset: 20%

Model Selection - Chosen Models for Training and Comparison
<img width="697" height="304" alt="image" src="https://github.com/user-attachments/assets/ad39e738-66d3-4e59-aab0-7c6a2c8f34a4" />

Model Hyperparameter-Tuning - Search for best params
<img width="830" height="424" alt="image" src="https://github.com/user-attachments/assets/f6cb4c0f-c939-4ed3-8198-21a370d0db7f" />

Model Final - After applying best params
<img width="838" height="409" alt="image" src="https://github.com/user-attachments/assets/a381f683-d6e8-4cd5-b4fc-e5d026170ccf" />

### Evaluation

<img width="685" height="400" alt="image" src="https://github.com/user-attachments/assets/ce954c71-ec44-4a97-bc83-c95d9ed30868" />
<img width="812" height="399" alt="image" src="https://github.com/user-attachments/assets/43f94754-cb4a-4f04-81a1-bff5066aa20f" />

Cross-Validation on Unseen Data (test dataset 20%)

<img width="449" height="350" alt="image" src="https://github.com/user-attachments/assets/e43dbc27-6bfb-4a79-ab0d-fc8f38aa0b44" />



## Recommendation and Analysis
**XGBoost Model:**
* Test RMSE: 0.4750
* R-squared: 0.9325
* The predicted vs. actual plot shows a general trend following the diagonal line, indicating that predictions roughly correspond to actual values.
* However, there is noticeable scatter around the line, especially for lower and higher values, suggesting the model has some difficulty capturing extreme values accurately.

**Random Forest Model:**
* Test RMSE: 0.4691
* R-squared: 0.9342 (better predictive accuracy and can explain slightly larger proportion of variance)
* Similar to XGBoost, the predicted vs. actual plot exhibits an overall alignment with the diagonal, but with visible spread and deviations.
* Predictions are less precise at the extremes, showing some under- and over-prediction patterns.

Both models outperform typical baseline approaches significantly. Random Forest achieves a marginally better RMSE (0.4691 vs. 0.4750) and R-squared (0.9342 vs. 0.9325), indicating slightly better overall fit and predictive accuracy on the test set. Residual distributions for both models suggest stable and reliable predictions without large error spikes.

### Conclusion:
Based on these metrics, the **Random Forest model** appears to perform slightly better than the XGBoost model on this dataset for predicting log_loves_count.

**SHAP Explanation**

<img width="849" height="451" alt="image" src="https://github.com/user-attachments/assets/0bbb1227-a5ad-4e70-b6e4-19afaf29f402" />

Both models captured the same top three most influential features for predicting high loves_count:
* log_reviews (no. of reviews)
* popularity_ratio (loves_count/no. of reviews)
* brand_name_encoded (mean of loves_count)
Middle-value features like size_value, price do contribute meaningfully but their impact is more situational
Low-value features (like child_count, online_only) show very narrow SHAP spread — low influence
Both models rely heavily on user engagement signals (reviews, popularity ratios).
Feature effects are mostly aligned, but Random Forest seems to pick up more on log_popularity_ratio, whereas XGBoost leans slightly more on ratings.


## AI Ethics
1. Privacy - Dataset does not contain any personal identifiable information or sensitive user data. Since no personal data is involved, there are minimal concerns regarding privacy.
2. Fairness - Dataset does not contain any factors such as race, gender, age or any demographics attributes that could introduce bias into model's prediction. This reduces the risk of creating biased prediction that could unfairly favor certain groups.
3. Accuracy - Dataset is as per Kaggle's repository collected via Scraper in March 2023 so accuracy of predictions is limited by data available at that time. Cross-validation is performed showing that the model is reliable based on these tests.
4. Accountability - Dataset does not include historical time-based data. This means the model cannot capture the full dynamic nature of how a product's popularity have evolved over time e.g. newer product may not have  as many loves_count as product have been available for longer period. Also, the model is designed to provide broad-based insights without specifically targetting any product categories, reducing the risk of overfitting or overly narrow predictions. However, accountability becomes relevant if the model's outputs are used to make real-world decisions so in such cases, it's important to provide ongoing monitoring to ensure model's predictions align with real-time data. 
6. Transparency - SHAP is used to explain the results returned by both XGBoost and Random Forest Regressor model which are considered black-box models. SHAP helps to explain the contributions of each feature making the model more interpretable.

## Source Codes and Datasets 
https://github.com/kelynz/itd214proj
