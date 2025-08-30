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
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

## Recommendation and Analysis
Explain the analysis and recommendations

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

## AI Ethics
Discuss the potential data science ethics issues (privacy, fairness, accuracy, accountability, transparency) in your project. 

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

## Source Codes and Datasets
Upload your model files and dataset into a GitHub repo and add the link here. 
https://github.com/kelynz/itd214proj
