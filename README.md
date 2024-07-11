# Insurance Claim Prediction Project

## Overview

This project aims to build predictive models to determine the claim status for a tour insurance firm. The firm has been facing higher claim frequencies, and the goal is to develop models that predict claim status and provide actionable insights to the management. The models used in this project are Classification and Regression Trees (CART), Random Forest (RF), and Artificial Neural Network (ANN). The performance of these models is compared based on their accuracy, confusion matrix, ROC curve, and AUC score on both train and test datasets.

## Table of Contents
1. Data Ingestion
2. Data Split
3. Model Building
4. Performance Metrics
5. Final Model Selection
6. Business Insights and Recommendations

## Data Ingestion

### Description
- **Dataset**: The dataset contains 3000 rows and 10 columns.
- **Null Values**: No missing values in the dataset.
- **Duplicates**: 139 duplicate rows were found but not removed due to lack of customer identification details.
- **Outliers**: Significant number of outliers in the dataset. Boxplots depicting outliers for every variable is shown below.

![image](https://github.com/user-attachments/assets/e01a6d36-e166-466e-9c28-efb94cce7cbf)

![image](https://github.com/user-attachments/assets/18860067-32d7-480c-91b9-3d18f65dc4e3)

![image](https://github.com/user-attachments/assets/53afe951-3f22-44c3-8696-3f7b583fed51)

![image](https://github.com/user-attachments/assets/38824d46-32ad-435b-9920-6784bb141dd6)

### Data Types
- The dataset contains `float64`, `int64`, and `object` data types.
- Categorical variables were converted to `int64` using `pd.Categorical` function.
- Column `Agency_Code` was removed due to insignificance.

### Exploratory Data Analysis (EDA)
- Pair plots, scatter plots, correlation heatmaps, and violin plots were used to visualize relationships between variables.

![image](https://github.com/user-attachments/assets/00246cb9-565d-4360-9bbb-306d90a28197)

![image](https://github.com/user-attachments/assets/5f8b431d-0e55-4959-a347-ba2345e82f4b)

![image](https://github.com/user-attachments/assets/b5e8af39-57da-4d52-97fc-6cd68b036d71)

## Data Split

- The dataset was split into training and testing sets with a 70-30 split ratio for all three models.

## Model Building

### Models Used
1. **Classification and Regression Trees (CART)**
2. **Random Forest (RF)**
3. **Artificial Neural Network (ANN)**

### Preprocessing
- Categorical variables were converted to numerical values before model building.

## Performance Metrics

### Confusion Matrix

![image](https://github.com/user-attachments/assets/136be67a-ed2d-4f2c-82a8-c937ae615741)

The confusion matrix for each model on train and test sets are as follows:

#### CART
- **Train Set**: TP: 1340, FP: 131, FN: 268, TN: 361
- **Test Set**: TP: 548, FP: 57, FN: 165, TN: 130

#### Random Forest
- **Train Set**: TP: 1468, FP: 3, FN: 8, TN: 621
- **Test Set**: TP: 536, FP: 69, FN: 164, TN: 131

#### ANN
- **Train Set**: TP: 1094, FP: 377, FN: 24, TN: 227
- **Test Set**: TP: 462, FP: 143, FN: 123, TN: 172

### Performance Metrics
The performance of each model is evaluated using Recall, Precision, Accuracy, and F-measure:

#### CART
- **Train Set**: Recall: 0.57, Precision: 0.73, Accuracy: 0.81, F-measure: 0.64
- **Test Set**: Recall: 0.44, Precision: 0.70, Accuracy: 0.75, F-measure: 0.54

#### Random Forest
- **Train Set**: Recall: 0.99, Precision: 1.00, Accuracy: 0.99, F-measure: 0.99
- **Test Set**: Recall: 0.44, Precision: 0.66, Accuracy: 0.74, F-measure: 0.53

#### ANN
- **Train Set**: Recall: 0.64, Precision: 0.55, Accuracy: 0.71, F-measure: 0.57
- **Test Set**: Recall: 0.58, Precision: 0.52, Accuracy: 0.70, F-measure: 0.56

### AUC - ROC Curve
- **CART**: Train AUC: 0.864, Test AUC: 0.795
Train AUC:

![image](https://github.com/user-attachments/assets/f080879e-5908-497f-ad14-1fb9bb95beaf)

Test AUC:

![image](https://github.com/user-attachments/assets/df3ed638-fc33-42e7-99a1-a8c7a1ddda44)

- **Random Forest**: Train AUC: 1.000, Test AUC: 0.798
Train AUC:

![image](https://github.com/user-attachments/assets/9cd20c66-b19f-4516-ab4f-6e95f5fc1f3b)

Test AUC:

![image](https://github.com/user-attachments/assets/21a18ace-079c-4082-8925-af94f18ece16)

- **ANN**: Train AUC: 0.773, Test AUC: 0.730
Train AUC:

![image](https://github.com/user-attachments/assets/b6e8a6af-2df0-4fd4-8297-3ba3a58d3e95)

Test AUC:

![image](https://github.com/user-attachments/assets/387729a5-1f98-42fa-ab8b-44f01f201bc8)

## Final Model Selection

The following table summarizes the performance of all models:

| Metric       | CART (Train) | CART (Test) | RF (Train) | RF (Test) | ANN (Train) | ANN (Test) |
|--------------|---------------|-------------|-------------|-----------|--------------|------------|
| Recall       | 0.57          | 0.44        | 0.99        | 0.44      | 0.64         | 0.58       |
| Precision    | 0.73          | 0.70        | 1.00        | 0.66      | 0.55         | 0.52       |
| Accuracy     | 0.81          | 0.75        | 0.99        | 0.74      | 0.71         | 0.70       |
| F-measure    | 0.64          | 0.54        | 0.99        | 0.53      | 0.57         | 0.56       |

Based on the above comparison, the **Artificial Neural Network (ANN)** model is selected as the best model due to its balanced performance on both train and test sets.

## Business Insights and Recommendations

- **Claim Status Prediction**: The target variable is Claim Status, with 0 indicating no claim and 1 indicating a claim.
- **Claim Frequency**: Approximately 70% of the customers are likely to claim their tour insurance, explaining the higher claim frequency.
- **Premium Adjustment**: The firm should consider revisiting and possibly increasing premium rates due to the high likelihood of claims.
- **Reinsurance Strategy**: Increasing the amount of risk ceded to reinsurers can mitigate adverse financial impacts.

These insights can help the insurance firm in making informed decisions to manage claim frequencies and financial risks effectively.
