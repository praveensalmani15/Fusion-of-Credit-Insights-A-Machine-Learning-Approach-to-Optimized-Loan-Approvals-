# Fusion-of-Credit-Insights-A-Machine-Learning-Approach-to-Optimized-Loan-Approvals-

**Problem Statement**

In the highly competitive financial sector, banks are under constant pressure to 
make prompt and accurate lending decisions to minimize risks and enhance profitability. 
The primary challenge is to accurately predict loan approval outcomes in spite of the 
complexity of applicants' financial histories and diverse credit behaviors. This project seeks 
to develop an advanced machine learning model that leverages the power of integrated 
internal banking data and external credit bureau insights to predict loan approval with 
precision. By harnessing this dual-data approach, the model will empower the bank to 
streamline its lending process, reduce default rates, and enhance customer satisfaction, all 
while ensuring compliance with regulatory standards. This solution will not only hone the 
bank's decision-making process but also set a new benchmark for intelligent, data-driven 
lending in the financial industry. 

# Loan Approval Prediction: Merging Internal Bank Data with External Credit Card Insights

## Project Overview

This project focuses on building predictive models to prioritize loan approvals based on internal bank data and external credit card data. The goal is to identify two classes of customers for loan approval:

- **Class 0**: First priority for loan approval
- **Class 1**: Second priority for loan approval

### Data Merging and Preprocessing

1. **Data Sources**: 
   - The dataset consists of two parts: internal bank data and external credit card data, which were merged on the `prospect_id` column using an inner join.

2. **Handling Missing Values**:
   - Converted placeholder value `-99999` to NaN.
   - Dropped columns based on missing values:
     - **Numerical columns**: Dropped if more than 25% of the values were missing.
     - **Categorical columns**: Dropped if more than 60 values were missing.
   - Missing values were filled:
     - **Median** for most columns.
     - **`max_deliq_12mts`** column was filled with 0.

3. **Feature Engineering**:
   - Dropped the `prospect_id` column as it was no longer needed.
   - The target variable, `approved_flag`, contained four unique values, which were converted into two classes:
     - **Class 0**: High-priority customers for loans.
     - **Class 1**: Secondary-priority customers for loans.

4. **Data Encoding and Splitting**:
   - Encoded categorical columns using appropriate encoding techniques.
   - Combined numerical and encoded categorical columns to create feature variables.
   - Split the data into training (70%) and testing (30%) sets.
   - Applied scaling to the training set for better model performance.

## Models and Performance Metrics

### Base Model: Logistic Regression

- **Accuracy**: 0.86
- **Recall for Class 0**: 0.95
- **Recall for Class 1**: 0.58

### Model Performance (After Tuning)

| Model                 | Accuracy | Recall (Class 0) | Recall (Class 1) |
|-----------------------|----------|------------------|------------------|
| **Random Forest**      | 0.88     | 0.95             | 0.68             |
| **Random Forest (Tuned)** | 0.88  | 0.94             | 0.70             |
| **Decision Tree**      | 0.83     | 0.89             | 0.67             |
| **Decision Tree (Tuned)** | 0.88  | 0.94             | 0.70             |
| **ADA Boost**          | 0.87     | 0.94             | 0.66             |
| **ADA Boost (Tuned)**  | 0.87     | 0.94             | 0.67             |
| **Gradient Boost**     | 0.88     | 0.95             | 0.68             |
| **Gradient Boost (Tuned)** | 0.89 | 0.95             | 0.71             |
| **XGBoost**            | 0.88     | 0.94             | 0.71             |
| **XGBoost (Tuned)**    | 0.88     | 0.94             | 0.71             |

### Performance Summary

- **Best Performance**: Gradient Boost (Tuned)
  - Accuracy: 0.89
  - Recall (Class 0): 0.95
  - Recall (Class 1): 0.71

The key validation metric for this project is **recall**, as the focus is on correctly identifying both high-priority and secondary-priority customers for loan approval.

## Conclusion

This project demonstrates a thorough end-to-end approach in merging diverse datasets, handling missing values, feature engineering, and evaluating model performance. The final tuned models, especially Gradient Boost and XGBoost, provide a robust solution for loan prioritization.

## Dataset Source: https://www.kaggle.com/datasets/saurabhbadole/leading-indian-bank-and-cibil-real-world-dataset