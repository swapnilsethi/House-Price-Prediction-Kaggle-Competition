# House Price Predication using Random Forest and XGBoost 

## Content

- [Personal Goal](###Personal-Goal)
- Problem Statement
- Dataset
- Exploratory Data Analysis
- Feature Enginnering
- Feature Selection
- Predications using Random Forest Model with hyperparameter tuning
- Predications using XGBoost Model with hyperparameter tuning
- Conclusion
- Future Scope
- Bibliography


### Personal Goal

This is my first project into predicative data science. The goal of this project is to learn about the data science project lifecycle, feature engineering and feature selection concepts, model design, hyperparameter tuning using cross validation methodologies, and so on.

### Problem Statement 

Predict houses sales price using suitable machine learning model. This is a Kaggle [compitation](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/overview) question. 

### Dataset 

2 datasets are provided - [Train](https://github.com/swapnilsethi/Stat-5000/blob/main/train.csv) and [Test](https://github.com/swapnilsethi/Stat-5000/blob/main/test.csv)

There are total 79 features in dataset which describe every aspect of residential homes in Ames, Iowa. 

### Exploratory Data Analysis 

1. Went through features and tried to understand them logically
2. Looked for null values and calculated their percentages presence.
3. Tried to understand relationship between null values and dependent variable (SalePrice)
4. Explored on numerical features
5. Have explored on temporal features and their relationship with dependent variable (SalePrice)
   Findings: 1. Data is available for houses sold between 2006 and 2010.
             2. Some of the houses are too old (built in 1872, and so on)
             3. House Sale Price is in negative correlation with yearsold.
             4. Hose prices are decreasing as per house age increases. 


