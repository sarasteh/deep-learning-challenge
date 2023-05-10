# deep-learning-challenge
 Here ,using machine learning and neural networks, we want to select the applicants for funding with the best chance of success in their ventures. We create a binary classification model that can predict if a funded organization will be successful based on the features in the dataset
The resource file contains more than 34,000 organizations that have received funding over the years. 

## Data Analysis
Within this dataset are a number of columns that capture metadata about each organization, such as:
- EIN and NAME—Identification columns
- APPLICATION_TYPE—Alphabet Soup application type
- AFFILIATION—Affiliated sector of industry
- CLASSIFICATION—Government organization classification
- USE_CASE—Use case for funding
- ORGANIZATION—Organization type
- STATUS—Active status
- INCOME_AMT—Income classification
- SPECIAL_CONSIDERATIONS—Special considerations for application
- ASK_AMT—Funding amount requested
- IS_SUCCESSFUL—Was the money used effectively

All columns except EIN, NAME, and IS_SUCCESSFUL are used as features(shown in the following table). 'IS_SUCCESSFUL' is used as the target for our classifier model. It has 1, and 0 values which are used to classify applicants into two different groups. Looking at the total numbers of different classes (1: 18261,  0 :16038), we can assume that training data is balanced.

![Figure.1](images/data.png)
