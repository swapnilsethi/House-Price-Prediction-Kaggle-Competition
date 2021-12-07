# House Price Predication using Random Forest and XGBoost 

## Content

- [Personal Goal](#Personal-Goal)
- [Problem Statement](#Problem-Statement)
- [Dataset](#Dataset)
- [Exploratory Data Analysis](#Exploratory-Data-Analysis)
- [Feature Enginnering](#Feature-Engineering)
- [Feature Selection](#Feature-Selection)
- [Predications using Random Forest Model with hyperparameter tuning](#Predications-using-Random-Forest-Model-with-hyperparameter-tuning)
- [Predications using XGBoost Model with hyperparameter tuning](#Predications-using-XGBoost-Model-with-Hyperparameter-tuning)
- [Conclusion](#Conclusion)
- [Future Scope](#Future-Scope) 
- [Bibliography](#Bibliography)


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
   - Data is available for houses sold between 2006 and 2010.
   - Some of the houses are too old (built in 1872, and so on)
   - House Sale Price is in negative correlation with yearsold.
   - Hose prices are decreasing as house age increases.
6. Explored and tried to understand relationship between rest numerical feature with [Pairplot](https://github.com/swapnilsethi/Stat-5000/blob/main/Pairplot.png) and correlation Matrix (Have used [Heatmap](https://github.com/swapnilsethi/Stat-5000/blob/main/Cormat.png) to visualize it).
7. Explored and tried to understand relationship between discrete features and dependent variable(SalePrice) using Bar chart.
8. Explored and tried to understand distribution of continuous features using Histogram.
9. Desiged box plots to understand outliers in each continuous feature.
   
   Findings: 
   - There are no outliers in dependent variable (SalePrice)
   - here are many outliers in features, I will deal with them in feature engineering section.
10. Have explored and tried to understand categorical features. Tried to understand relationship between in each sub-category in feature/catrgory with dependent variable(SalePrice).
   
### Feature Engineering ([Code](https://github.com/swapnilsethi/Stat-5000/blob/main/Feature_Engg.ipynb))

1. Combined Train and Test dataset to perform common operations
2. Removed columns having more than 80% null values
3. Handled null values in categorical features 
   - Replaced with 'missing' label and checked accuracy of model
   - Replaced with mode value of respective features and checked accuracy of model
   - finding:  Gained acccuracy of 85% through model 1 and 75.6% through model 2.
4. Handled null values in numerical features
   - Replaced all values with median values
   - Future Scope: Examine each feature to see if replacing it with 0 or another value is preferable rather than median values.
5. Have calculated age of house, duration from last modification, etc. and have dropped actual year columns. (Except house sold year) 
6. Have replaced all uncomman sub-categories in categorical features with 'rare_val' label
7. Have converted all categorical values with numerical values.
   - Have performed target encoding.
   - Future Scope:  There are many ways to do this like one One Hot Enconding, Dummy Encoding, Effect Encoding, Hash Encoding, etc. Will try with them and analyze model accuracy.
8. Seperated Training and Target datasets and generated CSV files. ([X_train.csv](https://github.com/swapnilsethi/Stat-5000/blob/main/X_train.csv), [X_Test.csv](https://github.com/swapnilsethi/Stat-5000/blob/main/X_test.csv))

### Feature Selection
Have performed but didn't worked well. Still exploring.

### Predications using Random Forest Model with hyperparameter tuning ([Code](https://github.com/swapnilsethi/Stat-5000/blob/main/RF_Model_and_Predictions.ipynb))

1. Divided training dataset in two section (X_train, X_test)
2. Designed Base model with 100 decision trees and calculated RMSE. Achieved RMSE of 0.1398.
3. Plotted single decision tree with then help of Graphviz to understand what happeing under the hood! ([Article Link](https://towardsdatascience.com/visualizing-decision-trees-with-python-scikit-learn-graphviz-matplotlib-1c50b4aa68dc))  
4. Predicated Sales Price of actual Test houses and uploaded solution on Kaggle. Got 0.14916 RMSE (Rank- 2820)
5. Performed hyper parameter tuning using Random Search method with K-fold cross validation to avoid overfitting issue. 
6. Performed Grid Search with K-fold cross validation. Got same accuracy as Random Search due to small dataset. 

### Predications using XGBoost Model with Hyperparameter tuning ([Code](https://github.com/swapnilsethi/Stat-5000/blob/main/Model_with_XGBoost.ipynb))

1. Divided training dataset in two section (X_train, X_test)
2. Desinged base model with default parameters and calculated RMSE. Achived RMSE of 0.1380. 
3. Predicated Sales Price of Actual Test houses and uploaded solution on Kaggle. Got 0.13354 RMSE (Rank- 1678)
4. Performed hyper parameter tuning using Random Search method. Got same RMSE.

### Conclusion
1. Due to small dataset hyper parameter tuning doesn't help to improve peformace of model
2. XGBoost worked well in this case as it combines results along the way rather than combining results at the end of the process (by averaging or "majority rules") like Random Forest
3. Boosing algoritms redudes bias (amd in some extent variance as well) but RF model works by reducing variance. In my case, I data had both high variance and high bias hence Boosting model worked well than the RF model.

### Bibliography

1. [Kaggle Problem Statement](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/overview)
2. [Data Science Project lifecycle](https://medium.com/co-learning-lounge/complete-data-science-project-life-cycle-9eae6e4ed4c9)
3. [Engineering Statistic Handbook](https://www.itl.nist.gov/div898/handbook/index.htm)(General Concepts in Analysis)
4. [Fundamental Techniques of Feature Engineering](https://towardsdatascience.com/feature-engineering-for-machine-learning-3a5e293a5114)
5. [Normalization and Algorithm Selection for unsupervised outlier paper](https://www.monash.edu/business/ebs/research/publications/ebs/wp16-2018.pdf)
6. [Feature Scaling](https://towardsdatascience.com/how-to-differentiate-between-scaling-normalization-and-log-transformations-69873d365a94)
7. [Principle Component Analysis](https://towardsdatascience.com/a-one-stop-shop-for-principal-component-analysis-5582fb7e0a9c)
8. [Scikit learn Supervised Learning Documentation](https://scikit-learn.org/stable/supervised_learning.html#supervised-learning)
9. [Decision Tree](https://towardsdatascience.com/decision-tree-ba64f977f7c3)
10. [Geeks for Geeks ML concepts](https://www.geeksforgeeks.org/machine-learning/?ref=shm)
11. [Random Forest Concept](https://towardsdatascience.com/random-forest-in-python-24d0893d51c0)
12. [Ways to visualize Decision Tree in Random Forest](https://towardsdatascience.com/4-ways-to-visualize-individual-decision-trees-in-a-random-forest-7a9beda1d1b7)
13. [visualize Decision Tree with python](https://towardsdatascience.com/visualizing-decision-trees-with-python-scikit-learn-graphviz-matplotlib-1c50b4aa68dc)
14. [HyperParameter Tuning with RF](https://towardsdatascience.com/hyperparameter-tuning-the-random-forest-in-python-using-scikit-learn-28d2aa77dd74)
15. [Feature Selection usinh Random Forest](https://towardsdatascience.com/feature-selection-using-random-forest-26d7b747597f)
16. [Datacamp XGBoost Tutorial](https://www.datacamp.com/community/tutorials/xgboost-in-python)
17. [XGBoost Feature Importance](https://mljar.com/blog/feature-importance-xgboost/)
18. [Github Syntax Documentation](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#section-links)
19. [Stackoverflow](https://stackoverflow.com)(For every small issue faced in coding)
