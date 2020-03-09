![alt text](https://github.com/kirahman2/fraud_detection/blob/master/images/creditcardfraudimage.jpg)
# This $190 Billion A Year Problem Is Costly. How Can Banks Better Predict Fraudulent Credit Card Transactions To Save You Money?

## Introduction
Detecting fraudulent credit card transactions is very challenging. In this project I explore a variety of features and models to determine which combination best predicts fraudulent card transactions. After parsing through much ambiguity, I manage to create and remove a number of features to improve the model score. 

## Data
This real life dataset comes from a Kaggle competition hosted by IEEE Computational Intelligence Society and Vesta. The dataset is comprised of 432 features and 590,540 rows. Some important features include basic credit card information such as transaction type (debit or credit), email address linked to card, product purchased and other anonymous features meant to randomize the personal information of the public [data](https://www.kaggle.com/c/ieee-fraud-detection/data).


## Preprocessing
* Filled missing data for 197 columns with each column's mode value.
*Dropped 214 columns missing more than 50% of data.
*Fixed “nan” string values and converted them to np.nan values. 
*Filled NaN values with “missing” in P_emaildomain feature. 
*Downsampled majority data from 569,877 to 95,000 using RandomUnderSampler.
*Upsampled minority data from 20,663 to 95,000 using SMOTE. 

## Exploratory Data Analysis
### Email Provider
![alt text]()
![alt text]()
![alt text]()
![alt text]()
### Address
![alt text]()
![alt text]()
![alt text]()
### Debit/Credit
![alt text]()
![alt text]()


## Modeling
![alt text]()

## Conclusion

