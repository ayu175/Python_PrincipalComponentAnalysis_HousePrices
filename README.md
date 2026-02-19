# **House Price Prediction Using PCA and Multiple Linear Regression**

## **Overview**
This project focuses on predicting house prices using principal component analysis (PCA) and multiple linear regression based on property and neighborhood characteristics. PCA was used to reduce dimensionality and multicollinearity, and the regression model was evaluated using R², RMSE, and MSE to assess predictive performance. The results provide insights for real estate pricing, valuation, and investment decision-making.

### **Programming Language**
Python

### **Skills Showcased**
This project demonstrates proficiency in several key areas:

#### **1. Data Preparation & Feature Engineering**
Selected property-level and neighborhood-level predictors (e.g., square footage, crime rate, school rating, distance to city center, amenities). Standardized numerical features and prepared data for PCA and regression modeling.

#### **2. Dimensionality Reduction (Principal Component Analysis)**
Applied PCA to transform correlated predictors into uncorrelated principal components. Retained four principal components using the Kaiser rule, capturing 51.89% of total variance, reducing multicollinearity and simplifying the regression model.

#### **3. Multiple Linear Regression Modeling**
Built a multiple linear regression model using the retained principal components to predict house prices. Used backward stepwise elimination to optimize model predictors and ensure statistical significance.

#### **4. Model Evaluation & Validation**
Split the dataset into 60% training and 40% validation sets. Evaluated model performance using:
##### • R² and Adjusted R²
##### • Mean Squared Error (MSE)
##### • Train vs. validation performance to assess overfitting

Key results:
R² ≈ 0.40, indicating the model explains ~40% of price variance
Similar MSE on training and validation sets, suggesting stable generalization

#### **5. Statistical Assumption Testing**
Evaluated regression assumptions including linearity, homoscedasticity, normality of residuals, independence of errors (Durbin–Watson), and multicollinearity. Identified violations and discussed potential transformations and modeling improvements.

#### **6. Business Insight & Interpretation**
Interpreted regression coefficients and principal components to explain how underlying property and neighborhood factors influence house prices. Discussed trade-offs between dimensionality reduction and predictive accuracy.

#### **7. Real Estate Strategy Recommendations**
Provided recommendations for real estate organizations, including:
##### • Using the model as a pricing and valuation decision-support tool
##### • Collecting additional data to improve predictive accuracy
##### • Exploring advanced models (e.g., nonlinear models, ensemble methods)
##### • Regular model retraining for market shifts
