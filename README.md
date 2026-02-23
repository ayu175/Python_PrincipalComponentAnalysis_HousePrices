# Housing Market Dimensionality Analysis

How accurately can we predict house prices using principal component analysis and multiple linear regression based on property and neighbourhood characteristics?

This project develops a predictive model for residential house prices by reducing an 11-variable feature set into principal components, then applying multiple linear regression to assess which underlying dimensions of property and neighbourhood characteristics most influence pricing. The goal is to support data-driven decisions in real estate pricing, investment, and property valuation.

## Key Findings

- **4 principal components** were retained using the Kaiser rule, together capturing **51.89% of total variance** across 11 original features (PC1: 21.27%, PC2: 11.77%, PC3: 9.60%, PC4: 9.25%)
- The final regression model achieved an **R² of 0.4029** on the training set and **0.3907** on the validation set, explaining roughly 40% of house price variance
- **Training MSE (13,522,383,192) and validation MSE (13,637,998,390) were nearly identical**, indicating the model generalizes reliably without overfitting
- All four principal components passed backward stepwise elimination (p < 0.05), confirming each contributed meaningfully to the model
- The regression equation is: **Price = $309,000 + ($54,730 × PC1) − ($19,220 × PC2) − ($12,080 × PC3) + ($35,760 × PC4)**
- A Durbin-Watson statistic of **1.991** confirmed no significant autocorrelation in the residuals
- Residual analysis revealed violations of linearity, homoscedasticity, and normality — suggesting the model underperforms at extreme price points and that log-transforming the target variable may improve future iterations

> **Interpretation:** An R² of ~0.40 is a realistic result for housing data, where unmeasured factors like interior condition, recent renovations, and buyer sentiment account for significant price variance. The near-identical train/validation MSE supports using this model as a reliable pricing baseline, particularly for mid-range properties, rather than a precise valuator.

## Dataset

Residential property dataset with **11 numeric continuous features** used as predictors:

| Feature | Level |
|---|---|
| Square Footage | Property |
| Backyard Space | Property |
| Age of Home | Property |
| Renovation Quality | Property |
| Crime Rate | Neighbourhood |
| School Rating | Neighbourhood |
| Distance to City Center | Neighbourhood |
| Employment Rate | Neighbourhood |
| Property Tax Rate | Neighbourhood |
| Local Amenities | Neighbourhood |
| Transport Access | Neighbourhood |

**Target variable:** House Price (continuous)

## Approach

Features were standardized (mean = 0, SD = 1) before applying PCA to ensure no single variable dominated variance due to scale differences. The Kaiser rule (eigenvalue > 1) was used to select four components for retention. A multiple linear regression model was then built on those components and refined using backward stepwise elimination, which iteratively removes predictors with p-values above 0.05. All four components were retained, each contributing a statistically significant effect on price.

Model assumptions were evaluated in full:

| Assumption | Result | Notes |
|---|---|---|
| Linearity | ❌ Violated | Residuals vs. fitted plot shows a funnel shape |
| Homoscedasticity | ❌ Violated | Slight funnel shape indicates heteroscedasticity |
| Independence of errors | ✅ Satisfied | Durbin-Watson = 1.991 |
| Normality of residuals | ❌ Violated | Omnibus and Jarque-Bera p ≈ 0.000; skew = 0.733, kurtosis = 3.664 |
| No multicollinearity | ✅ Satisfied | All correlations between PCs < 0.6 |

Transformations to the dependent variable (e.g., log price) are recommended to address the linearity, homoscedasticity, and normality violations in future iterations.

## Tools

Python · pandas · NumPy · scikit-learn (PCA, StandardScaler, train_test_split, metrics) · statsmodels · matplotlib · seaborn
