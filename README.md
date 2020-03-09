![alt text](https://github.com/kirahman2/fraud_detection/blob/master/images/creditcardfraudimage.jpg)
# This $190 Billion A Year Problem Is Costly. How Can Banks Better Predict Fraudulent Credit Card Transactions To Save You Money?

## Introduction
To predict fraudulent credit card transactions, I examined a variety of transaction attributes that clued me into which transactions are more likely to be fraudulent. 

## Data
This real life dataset comes from a Kaggle competition hosted by IEEE Computational Intelligence Society. The dataset is comprised of 432 features and 590,540 rows. Some important features include basic credit card information such as transaction type (debit or credit), email address linked to card, product purchased and other anonymous features designed to randomize the personal information of the public. https://www.kaggle.com/c/ieee-fraud-detection/data

## Preprocessing
For the data cleaning process, I followed the steps listed below.
* Dropped 214 columns that’s missing more than 50% of data.
* Imputed addr1, addr2, ProductCD, P_emaildomain, card1 - card6 and M1 - M6. 
* Downsampled the majority data from 569,877 to 95,000.
* Upsampled the minority data from 20,663 to 95,000.

## Exploratory Data Analysis
### Email Provider
![alt text](https://github.com/kirahman2/fraud_detection/blob/master/images/top10address.png)
![alt text](https://github.com/kirahman2/fraud_detection/blob/master/images/top10emailproviders.png)
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

