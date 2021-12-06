# House Price Predication using Random Forest and XGBoost 

## Content

- [Personal Goal](#Personal-Goal)
- [Problem Statement](#Problem-Statement)
- [Dataset](#Dataset)
- [Exploratory Data Analysis](#Exploratory-Data-Analysis)
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
All features are expalined in this [data_description](https://github.com/swapnilsethi/Stat-5000/blob/main/data_description.txt) file.

### Exploratory Data Analysis ([Code](https://github.com/swapnilsethi/Stat-5000/blob/main/House_Price_Predication_EDA.ipynb))

1. Tried to understand features logically
2. Looked for null values and calculated their percentages presence.
3. Understand relationship between null values and dependent variable (SalePrice)
4. Explored on numerical features.
5. Explored on temporal features and understood their relationship with dependent variable (SalePrice)
   Findings: 
             -  Data is available for houses sold between 2006 and 2010.
             -  Some of the houses are too old (built in 1872, and so on)
             -  House Sale Price is in negative correlation with yearsold.
             -  Hose prices are decreasing as house age increases.
6. Explored and tried to understand relationship between rest numerical feature with [Pairplot](https://github.com/swapnilsethi/Stat-5000/blob/main/Pairplot.png) and correlation Matrix (Have used [Heatmap](https://github.com/swapnilsethi/Stat-5000/blob/main/Cormat.png) to visualize it).
7. Explored and tried to understand relationship between discrete features and dependent variable(SalePrice) using Bar chart.
8. Explored and tried to understand distribution of continuous features using Histogram.
9. Desiged box plots to understand outliers in each continuous feature.
   Findings: 
             -  There are no outliers in dependent variable (SalePrice)
             -  There are many outliers in features, I will deal with them in feature engineering section.
9. Have explored and tried to understand categorical features. Tried to understand relationship between in each sub-category in feature/catrgory with dependent variable(SalePrice).
   
### Feature Engineering ([Code](https://github.com/swapnilsethi/Stat-5000/blob/main/Feature_Engg.ipynb))

1. Combined Train and Test dataset to perform common operations
2. Removed columns having more than 80% null values
3. Handled null values in categorical features 
            -  Replaced with 'missing' label and checked accuracy of model
            -  Replaced with mode value of respective features and checked accuracy of model
            -  finding:  Gained acccuracy of 85% through model 1 and 75.6% through model 2.
4. Handled null values in numerical features
            -  Replaced all values with median values
            -  Future Scope - Examine each feature to see if replacing it with 0 or another value is preferable rather than median values.
5. Have calculated age of house, duration from last modification, etc. and have dropped actual year columns. (Except house sold year) 
6. Have replaced all uncomman sub-categories in categorical features with 'rare_val' label
7. Have converted all categorical values with numerical values.
            - Have performed target encoding.
            - Future Scope-  There are many ways to do this like one One Hot Enconding, Dummy Encoding, Effect Encoding, Hash Encoding, etc. 
                           Try with them and analyze model accuracy.
8. Seperated Training and Target datasets and generated CSV files. ([X_train.csv](https://github.com/swapnilsethi/Stat-5000/blob/main/X_train.csv), [X_Test.csv](https://github.com/swapnilsethi/Stat-5000/blob/main/X_test.csv))
