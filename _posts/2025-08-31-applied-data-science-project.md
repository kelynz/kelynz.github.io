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
Cleaned up the dataset and prepared a final dataset with 22 features (target variable - log_loves_count).
Training Dataset: 80%    Test Dataset: 20%

### Data Preparation
* Data Exploration
  * Explore outliers
  * Look at data skewness
* Data Cleaning
  * Product Categories - Rectified mis-classification of products categories 
  * Product Size - Using regex to identify the numerical values and the units, putting it into numerical column (size_value) with a categorical column (unit)
* Data Preprocessing
  * Dropped identifier columns and irrelevant columns
  * Apply One-Hot encoding, Target encoding, Frequency Encoding
  * Log-Transformation
  * Imputing missing values
 
### Modelling

Model Selection - Chosen Models for Training and Comparison
<img width="697" height="304" alt="image" src="https://github.com/user-attachments/assets/ad39e738-66d3-4e59-aab0-7c6a2c8f34a4" />

### Evaluation

<img width="696" height="323" alt="image" src="https://github.com/user-attachments/assets/bd2ffdc1-c974-4758-ba31-3f8e8aed5269" />
<img width="624" height="363" alt="image" src="https://github.com/user-attachments/assets/bc2d189f-f883-4e5b-bf95-df7efaf26ce2" />
<img width="676" height="351" alt="image" src="https://github.com/user-attachments/assets/fd6bb61d-6511-417d-8b1b-7aca165fa9f5" />


## Recommendation and Analysis
**XGBoost Model:**
* Test RMSE: 0.8972
* R-squared: 0.7654
* The predicted vs actual plot shows a relatively strong alignment with the diagonal red dashed line, indicating that the model's predictions are closely matching the actual values.
* The residuals distribution for XGBoost has a skewness of -1.2599, indicating a slight leftward skew, and a kurtosis of 15.3195, suggesting the residuals have heavy tails (i.e., the model has some larger residual errors).

**Random Forest Model:**
* Test RMSE: 0.8951
* R-squared: 0.7665 (better predictive accuracy and can explain slightly larger proportion of variance)
* The predicted vs actual plot also shows strong alignment, with predictions closely following the red dashed line.
* The residuals for Random Forest have skewness of -1.5637, slightly more negative than XGBoost, and kurtosis of 13.6031, which is slightly lower than XGBoost, indicating less extreme values in the residuals.

### Conclusion:
Based on these metrics, the **Random Forest model** appears to perform slightly better than the XGBoost model on this dataset for predicting log_loves_count.

**SHAP Explanation**

<img width="605" height="427" alt="image" src="https://github.com/user-attachments/assets/08bc7bdf-ad4e-4572-9998-7d0287b89329" />

Both models captured the same top three most influential features for predicting high loves_count:
* log_reviews
* brand_name_encoded
* child_count
These features show a significant impact on the model outputs, as observed in the SHAP summary plots. 

For both models, log_reviews exhibits the highest variation in SHAP values, with positive values leading to higher predictions of loves_count. Similarly, brand_name_encoded and child_count also display strong influences, with varying degrees of effect as the feature values change.

The relationship between these features and the model's predictions remains consistent across both models, indicating that they are equally influential in predicting the target variable, loves_count.

## AI Ethics
1. Privacy - Dataset does not contain any personal identifiable information or sensitive user data. Since no personal data is involved, there are minimal concerns regarding privacy.
2. Fairness - Dataset does not contain any factors such as race, gender, age or any demographics attributes that could introduce bias into model's prediction. This reduces the risk of creating biased prediction that could unfairly favor certain groups.
3. Accuracy - Dataset is as per Kaggle's repository collected via Scraper in March 2023 so accuracy of predictions is limited by data available at that time. Cross-validation is performed by comparing between two strong models (XGBoost and Random Forest Regressor) showing that the model is reliable based on these tests.
4. Accountability - Dataset does not include historical time-based data. This means the model cannot capture the full dynamic nature of how a product's popularity have evolved over time e.g. newer product may not have  as many loves_count as product have been available for longer period. Also, the model is designed to provide broad-based insights without specifically targetting any product categories, reducing the risk of overfitting or overly narrow predictions. However, accountability becomes relevant if the model's outputs are used to make real-world decisions so in such cases, it's important to provide ongoing monitoring to ensure model's predictions align with real-time data. 
6. Transparency - SHAP is used to explain the results returned by both XGBoost and Random Forest Regressor model which are considered black-box models. SHAP helps to explain the contributions of each feature making the model more interpretable.

## Source Codes and Datasets 
https://github.com/kelynz/itd214proj
