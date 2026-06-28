# Lab 4: Regression Analysis with Regularization Techniques

Name: Ashish Mahajan  
Course: 2026 Summer - Advanced Big Data and Data Mining (MSCS-634-M20)

## Purpose
Lab compares Simple Linear Regression, Multiple Linear Regression, Polynomial Regression, Ridge Regression, and Lasso Regression using the Diabetes Dataset from scikit-learn.

## Dataset
- Dataset: Diabetes Dataset from sklearn
## Repository Structure
```text
Adv_Data_and_Mining_26_Lab_4/
|-- README.md
|-- requirements.txt
|-- lab4_regression_regularization_diabetes.ipynb
`-- screenshots/
    |-- README.md
    `-- captured PNG files
```

## Key Results

- Best model by Test RMSE: Best Lasso Regression, 53.1467
- Best model by Test R-squared: Best Lasso Regression, 0.4669
- Best Ridge alpha: 100
- Best Lasso alpha: 1
- Best mean cross-validation RMSE: Multiple Linear Regression, 54.6918
- Best Lasso mean cross-validation RMSE: 54.7113 with standard deviation 1.0319

## Key Insights

- Simple Linear Regression provided an interpretable baseline using only `bmi`, with Test RMSE 63.7325 and Test R-squared 0.2334.
- Multiple Linear Regression used all available features and improved the baseline to Test RMSE 53.8534 and Test R-squared 0.4526.
- Polynomial Regression increased model flexibility, but it did not improve test performance in this run. Degree 4 slightly increased Train R-squared while Test R-squared fell to 0.2023, suggesting overfitting.
- Ridge used L2 regularization to shrink coefficients. Alpha 100 produced its best Test RMSE of 53.4624 while retaining all 10 coefficients.
- Lasso used L1 regularization and produced the best held-out results at alpha 1, retaining 9 nonzero coefficients. At larger alpha values, more coefficients became zero and performance eventually declined.
- Multiple Linear Regression had the lowest mean cross-validation RMSE, but Best Lasso was only 0.0195 higher and had lower fold-to-fold variation.
- The Best Lasso actual-vs-predicted plot followed the overall positive trend but showed prediction errors at the target extremes, so the model does not explain all variation in disease progression.

## Final Recommendation

Based on the test metrics, cross-validation results, and actual-vs-predicted plots, I would select Lasso Regression with alpha 1 as the deployment candidate for this dataset and split. It had the lowest Test RMSE of 53.1467, the highest Test R-squared of 0.4669, and a mean cross-validation RMSE of 54.7113 that was nearly equal to the best cross-validation result. It also reduced one coefficient to zero, providing modest feature selection.
Test R-squared shows that substantial variation remains unexplained, and the prediction plot indicates errors at low and high target values. Additional validation and domain review would be needed before real clinical use.

## How to Run
```bash
jupyter notebook
```

Open `lab4_regression_regularization_diabetes.ipynb` in Jupyter Notebook.