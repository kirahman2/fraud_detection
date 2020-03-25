![alt text](https://github.com/kirahman2/fraud_detection/blob/master/images/creditcardfraudimage.jpg)
# This $190 Billion A Year Problem Is Costly. How Can Banks Better Predict Fraudulent Credit Card Transactions To Save You Money?

## Introduction
Detecting fraudulent credit card transactions is challenging. In this project I explore a variety of features and models to determine which combinations best predict fraudulent transactions. After parsing through much ambiguity, I manage to create new features resulting in a successful model. [Notebook/code](https://github.com/kirahman2/fraud_detection/blob/master/Fraud%20Detection%20Notebook.ipynb)

## Data
The dataset comes from a Kaggle competition hosted by IEEE Computational Intelligence Society and Vesta. It is comprised of 432 features and 590,540 rows. Some important features include basic credit card information such as transaction type (debit or credit), email address linked to card, product purchased and other anonymous features meant to randomize the personal information of the public. [data source](https://www.kaggle.com/c/ieee-fraud-detection/data)

## Preprocessing
* Dropped 214 columns missing more than 50% of data.
* Filled missing data for 197 columns with each column's mode value.
* Downsampled majority data from 569,877 to 95,000 using RandomUnderSampler.
* Upsampled minority data from 20,663 to 95,000 using SMOTE. 

## Exploratory Data Analysis
During the exploratory data analysis phase I hypothesized that an email provider associated with a card transaction is a potential predictor of fraudulent card transactions. Below we can see the top email providers in the dataset.

<p align="left">
  <img width="580" height="280" src="https://github.com/kirahman2/fraud_detection/blob/master/images/top10emailproviders.png">
</p>

With Gmail representing 228,355 records compared to Comcast at 7,888 records, I decided to bin less common email providers and calculate the ratio (fraud / not fraud) for each bin. Using the information here, I apply my findings directly to the model.

<p align="left">
  <img width="680" height="240" src="https://github.com/kirahman2/fraud_detection/blob/master/images/top6emailproviders_ratio.png">
</p>

## Modeling
### Imputed Features
In the dataset I imputed the features listed below. 
* Imputed (label encoded) 333 values from addr1
* Imputed (label encoded) 75 values from addr2
* Imputed (dummy variable) 5 values from ProductCD
* Imputed (dummy variable) 59 values from P_emaildomain
* Imputed (label encoded) 13,553 values from card1
* Imputed (label encoded) 500 values from card2
* Imputed (label encoded) 114 values from card3
* Imputed (dummy variable) 4 values from card4
* Imputed (label encoded) 119 values from card5
* Imputed (dummy variable) 4 values from card6
* Imputed (dummy variable) 2 values from each of M1 - M6

### Feature Engineering
The following features were created by calculating the probability of each unique value within each feature being fraudulent. 

* addr1_fe, addr2_fe, card2_fe, card3_fe, C1_fe, P_emaildomain_fe, card6_fe, V294_fe, V279_fe, C14_fe, V306_fe, D2_fe, D10_fe, card5_fe, V317_fe, V69_fe, D1_fe, D3_fe, D4_fe and D11_fe

### Dropped Features
The following features were dropped. 

* addr1, addr2, card2, card3, C1, V294, V279, C14, V306, D2, D10 and C4

The dataset used to train the model has a total of 291 predictors. I selected a 9/10 - 1/10 train-test split for the models. The results are show below.

## Results
| Model   | Performance | Performance with Hyperparam. Tuning | 
| :------------- |:-------------|:-----|
| Logistic Regression | 0.720 AUC| 0.798 AUC|
| Random Forest Classifier | 0.846 AUC| 0.861 AUC|
| XGB Classifier     | 0.819 AUC| 0.880 AUC|
| Cat Boost Classifier | 0.887 AUC| 0.908 AUC|

For the base model, I chose Logistic Regression. During the research process I discovered random forests are known to be the best model for detecting fraudulent card transactions. Considering this, I introduced XGBClassifier and CatBoost since they are tree based models. Of all models, CatBoostClassifier scored the highest. 

Below is the feature importance bar chart of CatBoostClassifier. We see that a number of engineered features became some of the most important for making accurate predictions. 

<p align="left">
  <img width="400" height="380" src="https://github.com/kirahman2/fraud_detection/blob/master/images/feature_importance.png">
</p>

## Conclusion
After reviewing the feature importance bar chart, it became apparent that one hot encoding features in the dataset proved to be very effective. Future iterations of this project would include revisiting EDA to uncover additional signal in features like addr1 and TransactionAmt to create new features. 
