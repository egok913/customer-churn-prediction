# Customer Churn Prediction in a Subscription-Based Service

## Project Overview

This project develops machine learning models to predict customer churn in a subscription-based service using the Telco Customer Churn dataset.

The main objective is to identify as many customers at risk of churning as possible. Because missing a potential churner can be more costly than contacting a customer who would not have churned, the project places particular emphasis on **recall and the F2 score**, while also considering accuracy and ROC-AUC.

The project compares traditional machine learning models, ensemble approaches, and a feed-forward neural network, and uses SHAP analysis to interpret model predictions.

## Dataset

The project uses the **Telco Customer Churn dataset**, containing 7,043 observations and 21 features.

After removing the irrelevant `customerID` field, the dataset contains customer characteristics and a binary `Churn` target.

The dataset itself is **not included in this repository**.

## Methodology

The analysis includes:

* Exploratory data analysis
* Data preprocessing and feature transformation
* Logistic Regression
* Random Forest
* XGBoost
* Ensemble methods
* Feed-forward neural network
* Autoencoder-based dimensionality reduction
* SHAP-based model interpretation

The shallow machine learning models were evaluated using three optimization objectives:

* Accuracy
* ROC-AUC
* F2 score

The F2 score was emphasized because the project prioritizes identifying customers who are likely to churn.

## Key Findings

The analysis found that:

* **XGBoost optimized for F2** provided the strongest overall balance for the project's objective.
* F2 optimization substantially increased positive-class recall compared with optimizing for accuracy.
* Logistic Regression and Random Forest produced competitive results.
* Ensemble stacking and voting methods did not substantially improve upon the strongest individual models.
* The feed-forward neural network did not meaningfully outperform the shallow machine learning models.
* Autoencoder-based dimensionality reduction did not improve model performance.
* SHAP analysis identified **MonthlyCharges** and **TotalCharges** as important features across models.
* **Contract** and **Tenure** were also important for several models.

### Selected Model Performance

| Model               | Optimization | Accuracy | ROC-AUC |       F2 |
| ------------------- | ------------ | -------: | ------: | -------: |
| Logistic Regression | Accuracy     |     0.80 |    0.83 |     0.54 |
| Logistic Regression | ROC-AUC      |     0.80 |    0.84 |     0.58 |
| Logistic Regression | F2           |     0.69 |    0.82 |     0.73 |
| Random Forest       | F2           |     0.73 |    0.83 |     0.70 |
| XGBoost             | ROC-AUC      |     0.72 |    0.84 |     0.72 |
| XGBoost             | F2           |     0.67 |    0.84 | **0.73** |

The F2-optimized Logistic Regression and XGBoost models achieved the highest reported F2 score of **0.73**. The project ultimately identifies **F2-optimized XGBoost** as the most suitable model for deployment based on its balance of recall and precision.

## Model Interpretation

SHAP analysis was used to understand which features contributed most strongly to model predictions.

The analysis highlighted:

* MonthlyCharges
* TotalCharges
* Contract
* Tenure

These findings were broadly consistent with the exploratory analysis, which indicated relationships between churn and factors such as short tenure, weaker contractual commitment, and pricing-related characteristics.

## Repository Contents

* `customer_churn_prediction.ipynb` — Main analysis notebook
* `customer_churn_report.pdf` — Project report
* `customer_churn_presentation.pptx` — Project presentation
* `README.md` — Project overview and documentation

## Conclusion

The project demonstrates an end-to-end customer churn prediction workflow, from exploratory analysis and preprocessing through model development, evaluation, and interpretability.

The results suggest that optimizing specifically for the business objective of identifying potential churners is more appropriate than relying on accuracy alone. F2-optimized XGBoost was selected as the most suitable final approach, while simpler models remained competitive.

The neural network and autoencoder experiments did not provide meaningful improvements over the shallow machine learning approaches.

## Limitations and Future Work

Potential future improvements include:

* Further model and hyperparameter optimization
* Additional feature engineering
* More extensive evaluation of threshold selection
* Testing on additional or more recent customer data
* Further investigation of model calibration and deployment considerations

## Author

Master's student / Data Science project
