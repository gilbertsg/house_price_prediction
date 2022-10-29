# Project 2 - Ames Housing Data and Kaggle Challenge
---


## Context & Problem Statement
---
**Context:** We are tasked to assist property agents in creating models for predicting the house prices in Ames (Iowa, USA). The models generated needs to be accurate, while still being explainable. We are also tasked to provide explanation for the most important factors in determining a house price, as well as provide a heuristic model (mental shortcuts) for quickly gauging the price of a house. The models will be used for the realtors in generating a baseline pricing for valuation of the house.

**Problem Statement:**
- Investigate the following questions on feature selection:
    - How well does the different regularization techniques (L1, L2, ElasticNet) work in selecting the best feature for prediction?
    - Which features can best predict house prices?
- Investigate the trade off between number of features versus the accuracy of the model
- Propose several methods for further feature engineering after feature selection through regularization.



## Project Summary and Conclusion
---
In this project, we are tasked to assist property agents in creating models for predicting the house prices in Ames (Iowa, USA). 

- **Data Pre-Processing:** The dataset were processed through the following processes:
    - Data cleaning were conducted on the provided data set. This is done by imputing values for all of the Null values in the data set.
    - All of the ordinal categorical variables were converted to its equivalent numerical scoring
    - All of the nominal categorical variable over one-hot encoded
- **Modelling:** Three types of regularization technique (Lasso, Ridge, and ElasticNet) were applied on the data set. Out of the three techniques, Lasso resulted in the high accuracy and the lowest number of features included. The Lasso model achieved an R2 of 0.892 in predicting the test dataset.
- **Most important features:** The two features that can best predict house price is the above ground living area as well as the overall quality of the house. It is followed by a series of features which measures the area and quality of various specific location / aspect of the house.
- **Accuracy-Complexity Tradeoff:** Assuming no overfitting, the accuracy of the model increases as the number of features included increases. This is the trade-off between accuracy and complexity. There is a diminishing returns to adding more features. It was found that using around 10 features already resulted in a model with an R2 of aroudn 0.8. This simple model can be used as a heuristic model for humans when comparing the prices of different houess.
- **Model Improvement:** Two methods for further improving the model were attempted:
    - Converting ordinal variables to non-linear
    - Removing outliers
    - A combination of both
- The techniques mentioned above resulted in significant improvement in accuracy as well as a reduction in number of features selected.
- **Final Model:** The final model has an R2 of 0.919 in predicting the test dataset, while using only ~ 50% of the potential variables from about ~68% of available features.

The table below summarizes all the models studied in this project. 

|No  | Regression Type                           |   Non-Zero Variables |   Non-Zero Features |      MAE |     RMSE |          R2 |      R2_adj |
|---:|:------------------------------------------|---------------------:|--------------------:|---------:|---------:|------------:|------------:|
|  1 | Baseline (mean)                           |                    0 |                   0 | 0.725674 | 0.966447 | -0.001048   | -0.001048   |
|  2 | Ridge                                     |                  191 |                  76 | 0.233155 | 0.328329 |  0.884464   |  0.872593   |
|  3 | ElasticNet                                |                  126 |                  59 | 0.230429 | 0.323886 |  0.887570   |  0.880207   |
|  4 | Lasso                                     |                  103 |                  57 | 0.226923 | 0.316802 |  0.892434   |  0.886743   |
|  5 | Lasso (with non-linear ordinal variables) |                   98 |                  56 | 0.217876 | 0.302574 |  0.901879   |  0.896952   |
|  6 | Lasso (with removal of outliers)          |                   92 |                  55 | 0.219964 | 0.307873 |  0.913873   |  0.909826   |
|  7 | Lasso (combined)                          |                   91 |                  52 | 0.215785 | 0.298797 |  0.918876   |  0.915107   |