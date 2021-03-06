# ImmoEliza_House_Prediction

# Description

Housing Prices Prediction is an essential element for an economy. Analysis of price ranges influence both sellers and buyers.Our project is mainly focused on prediction of prices against explanatory features that cover many aspects of houses. Also, this project creates a Linear Regression model to estimate the price of the house accurately with the given features.

# To Whom

['ImmoEliza'](https://immoelissa.be/) wants Belgium's House Prediction model to find and analyse the sales in Belgium.

# Objective

Be able to apply a linear regression in a real context & preprocess data for Machine Learning.

# How it Works?

We have collected the previously scraped, pre-processed  and analysed data. We again analysed the data for null values, how to handle categorical data, which features to be considered using Feature selection process etc. Once the final data is available, we have formatted by dividing into traning set and test set for machine to learn. Then, we tranined the model using machine learning algorithm which in this case is Linear Regression. 

<img src="https://github.com/FrancescoMariottini/Belgium-prices-prediction/blob/manasa/assets/images/flowchart.png" width="700" height="400">

1. Data Pre-processing and Cleaning
2. Feature Engineeing and Feature Selection
3. Linear Regression Model 
4. Evaluation


#### Data Pre-processing and Cleaning"
Originally all object values were converted into numerical (through aggregated values) but then kept as object to allow easier filtering within "Feature Engineeing and Feature Selection" module.
To improve the data quality (and model), median price by postcode was extracted from historical sales data (statbel) combined with postcodes information.
Later latitude and longitude were added as features for the *apartments* analysis.

##### Steps performed:
1. Aggregated parameter columns created for categorical values and for facades number (based on building subtype). 
2. Filling Not_a_Number with zeros
3. Outliers identification using Tukey fences due right-skewed distribution

Postcode was replaced by median price obtained from the official belgian statistics in a dedicated dataset (see data folder).

Used training and test dataset were generated by combining the following datasets:
1. results of [residential real estate analysis](https://github.com/FrancescoMariottini/residential-real-estate-analysis) project
2. official real estate selling data from [statbel](https://bestat.statbel.fgov.be/bestat/crosstable.xhtml?view=8b645a91-0bd8-468b-88f4-4430e923a579)
3. zipcode, latitude and longitude of Belgian municipalities from [zipcode-belgium](https://github.com/jief/zipcode-belgium) project


#### Feature Engineeing and Feature Selection

##### Steps performed:

1. Removed the features where the data was missing and irrelevant . 
2. Feature selection was done mostly using the Chi-squared contingency method which gives the list of features that are irrelevant for the model , and can be     
   removed from the dataframe. 
3. Utilising the pandas get_dummies class for one hot encoding on all the categorical columns to be used in the model.

#### Linear Regression Model application

We have started with ordinary least squares(OLS) using scikit's Linear Regression class on the dataset and observed that results are not so bad.Later tried applying polynomial regrssion using 5-fold cross-validation with degree 2 was better than linear regression (degree 1
) but was worse for degree 3 and higher. Then, we cleaned the data again with more features and applied polynomial regression with degree 2 itself. It is observed that for this dataset, simple linear regression is the best choise and we have applied.

#### Evaluation

Model evaluation is an essential part in machine learning process. It describes how well the model is performing in its predictions. Evaluation metrics changes according to the problem definition. The errors represents the variation of faults in its predictions. Thus, it becomes important to compare actual target with the predicted one. 

We have applied Regression metrics like Mean Absolute Error, Mean Squared Error, Mean Absolute Percentage Error and R-squared. R-squared is a statistical measure of how close the data to the fitted line. The higher the R-squared, the better the model fits the data. 

#### Inferences 
When considering all type of buildings, Test_RSquare increases from 0.47 to 0.51 when including the additional features (median price, latitude and longitude by postcode).
When considering only apartments, Test_RSquare decreases from  0.72 to 0.69 when including the additional features (median price, latitude and longitude by postcode).

#### Conclusions
Complete dataset with more data and variables ( new features) could improve the model effectiveness. 
E.g. there are not enough representative values for some postcodes in the scrapped dataset.
That would also allow a better selection of features in return which plays a vital role in increasing the model accuracy.
Better correlation is found using a subset including only apartments combined with official statistics data.

#### Future steps
Project is considered concluded and no additional resarch is foreseen.
However a few possible improvements are hereby suggested:
1. scrapping more data online including also other key parameters (e.g. building construction year)
2. make full use of other available reliable datasets (e.g. official statistics) to improve the model
3. explore different subset of data (e.g. by building type and status) to get accurate targeted results
