# House Price Predication using Random Forest and XGBoost 

## Content

- [Personal Goal](#Personal-Goal)
- [Problem Statement](#Problem-Statement)
- [Dataset](#Dataset)
- [Exploratory Data Analysis](#Exploratory-Data-Analysis)
- [Feature Enginnering](#Feature-Engineering)
- [Feature Selection](#Feature-Selection)
- [Predictions using Random Forest Model with hyperparameter tuning](#Predictions-using-Random-Forest-Model-with-hyperparameter-tuning)
- [Predictions using XGBoost Model with hyperparameter tuning](#Predictions-using-XGBoost-Model-with-hyperparameter-tuning)
- [Conclusion](#Conclusion)
- [Future Scope](#Future-Scope) 
- [Bibliography](#Bibliography)


### Personal Goal

This is my first project into the world of predictive data science. The purpose of this project is to gain knowledge of the data science project lifecycle, feature engineering and feature selection ideas, model construction, hyperparameter tuning using cross validation approaches, and so on.

### Problem Statement 

Predict sale price of a houses using a machine learning model. This is a Kaggle [competition](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/overview) question. 

### Dataset 

2 datasets are provided - [Train](https://github.com/swapnilsethi/Stat-5000/blob/main/train.csv) and [Test](https://github.com/swapnilsethi/Stat-5000/blob/main/test.csv)

There are total 79 features in dataset which describe every aspect of residential homes in Ames, Iowa. 
All features are expalined in this [data_description](https://github.com/swapnilsethi/Stat-5000/blob/main/data_description.txt) file.

### Exploratory Data Analysis ([Code](https://github.com/swapnilsethi/Stat-5000/blob/main/House_Price_Predication_EDA.ipynb))

1. I attempted to comprehend aspects in a rational manner.
2. Determined the presence of null values by calculating their percentages.
3. Understand relationship between null values and dependent variable (SalePrice)
4. Investigated numerical features.
5. Explored on temporal features and understood their relationship with dependent variable (SalePrice)
   
   Findings: 
   - Data for houses sold between 2006 and 2010 is available.
   - Some of the houses are too old (built in 1872, and so on)
   - House Sale Price is in negative correlation with yearsold.
   - As a house gets older, the cost of a hose decreases.
6. Using [Pairplot](https://github.com/swapnilsethi/Stat-5000/blob/main/Pairplot.png) and correlation Matrix (Have used [Heatmap](https://github.com/swapnilsethi/Stat-5000/blob/main/Cormat.png) to visualize it), I explored and attempted to identify the link between the remainder numerical features.
7. Using a bar chart, I explored and attempted to comprehend the link between discrete attributes and the dependent variable (SalePrice).
8. Using a histogram, I explored and attempted to comprehend the distribution of continuous features.
9. Created box plots to visualize outliers in each continuous feature
   
   Findings: 
   - There are no outliers in dependent variable (SalePrice)
   - There are several outliers in the features, which I will address in the feature engineering section.
10. Have investigated and attempted to comprehend categorical features. I tried to figure out what the relationship was between each sub-category in each feature/category and the dependent variable (SalePrice).
   
### Feature Engineering ([Code](https://github.com/swapnilsethi/Stat-5000/blob/main/Feature_Engg.ipynb))

1. To conduct common operations, combined the Train and Test datasets.
2. Columns with more than 80% null values are removed.
3. Handled null values in categorical features 
   - Replaced with 'missing' label and checked accuracy of model
   - Replaced with mode value of respective features and checked accuracy of model
   - finding:  Gained accuracy of 85% through model 1 and 75.6% through model 2.
4. Handled null values in numerical features
   - Replaced all values with median values
   - In the future, I'll Examine each characteristic to see if replacing it with 0 or another value, rather than median values, is desirable or not.
5. Have calculated age of house, duration from last modification, etc. and have dropped actual year columns. (Except house sold year) 
6. Have replaced all uncommon sub-categories in categorical features with 'rare_val' label
7. Have converted all categorical values with numerical values.
   - Have performed target encoding.
   - Future Scope:  There are many ways to do this like one One Hot Enconding, Dummy Encoding, Effect Encoding, Hash Encoding, etc. Will try with them and analyze model accuracy.
8. Seperated Training and Target datasets and generated CSV files. ([X_train.csv](https://github.com/swapnilsethi/Stat-5000/blob/main/X_train.csv), [X_Test.csv](https://github.com/swapnilsethi/Stat-5000/blob/main/X_test.csv))

### Feature Selection([Code](https://github.com/swapnilsethi/Stat-5000/blob/main/Feature_Selection_with_RF.ipynb))
Have tried but didn't worked well. Still exploring.

### Predictions using Random Forest Model with hyperparameter tuning ([Code](https://github.com/swapnilsethi/Stat-5000/blob/main/RF_Model_and_Predictions.ipynb))

1. Divided training dataset in two sections (X_train, X_test)
2. Designed Base model with 100 decision trees and calculated RMSE. Achieved RMSE of 0.1398.
3. Using Graphviz, I plotted a single decision tree to see what was going on underneath the hood! ([Article Link](https://towardsdatascience.com/visualizing-decision-trees-with-python-scikit-learn-graphviz-matplotlib-1c50b4aa68dc))  
4. Predicated Sales Price of actual Test houses and uploaded solution on Kaggle. Got 0.14916 RMSE (Rank- 2820)
5. To avoid overfitting, performed hyper parameter tweaking using the Random Search method with K-fold cross validation.
6. Performed Grid Search with K-fold cross validation. Due to the small dataset, the accuracy was the same as Random Search.

### Predictions using XGBoost Model with hyperparameter tuning ([Code](https://github.com/swapnilsethi/Stat-5000/blob/main/Model_with_XGBoost.ipynb))

1. Separated the training dataset into two parts (X_train and X_test).
2. Created a base model with default parameters and estimated the root mean square error. The RMSE was 0.1380. 
3. Predicted Sales Price of Actual Test Houses, published solution to Kaggle. Achived RMSE of 0.13354. (Rank- 1678)
4. Used the Random Search method to tune hyperparameters. The RMSE is same.

### Conclusion
1. Due to the small dataset, hyper parameter adjustment is ineffective in improving model performance. 
2. In this scenario, XGBoost performed well because it combines results along the way rather than at the conclusion of the process (through averaging or "majority rules"), as Random Forest.
3.  Boosting algorithms reduce bias (and to a lesser extent variance), whereas the RF model reduces variance. Because my data had both high variance and significant bias, the boosting model performed better than the RF model.

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
17. [XGBoost Documentation](https://xgboost.readthedocs.io/en/latest/parameter.html#general-parameters)
18. [HyperParameter Tuning with XGBoost](https://towardsdatascience.com/xgboost-fine-tune-and-optimize-your-model-23d996fab663)
19. [XGBoost Feature Importance](https://mljar.com/blog/feature-importance-xgboost/)
20. [Seaborn](https://seaborn.pydata.org/index.html), [Pandas](https://pandas.pydata.org/docs/user_guide/index.html), [Numpy](https://numpy.org/doc/1.21/user/basics.html), [Matplotlib](https://matplotlib.org/stable/plot_types/index) Documentation
21. [Github Syntax Documentation](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#section-links)
22. [Stackoverflow](https://stackoverflow.com)(For every small issue faced in coding)
