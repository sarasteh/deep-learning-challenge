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

## Machine Learning Process
> ### Preprocessing: 

To prepare data for training, first we need to clean and scale it. By looking at the number of unique values of categorical columns with more than 10 unique values, we regroup "rare" categorical variables together in a new value (‘other’). Next we encode all categorical variables.
The final step is scaling data using StandardScaler.

> ### Compile, Train, and Evaluate the Model

After cleaning and encoding the categorical variables, we have 43 features to use as inputs for our neural network model. The very first model is designed as shown in the following Figure (input nodes: 43, first layer nodes:80, second layer nodes:30, output node:1). Activation function for Input and hidden layers is ‘relu’ and for the output layer is ‘sigmoid’.
Parameters used to fit the models are: batch_size=20, epochs=100. We also create a callback that saves the model's weights every five epochs. The final results save and export to an HDF5 file (AlphabetSoupCharity.h5).

![Figure.2](images/firstmodel.png)

The evaluation on test data is as follows: 

![Figure.3](images/firstmodel_test.png)

## Optimize the Model
To Optimize the model we take following steps:

> Dropping 'STATUS',  'SPECIAL_CONSIDERATIONS' columns:

These two columns mostly have a single value, which makes them less useful for our training. They only add more complexity with not much information.
The same model, defined in the last section, applied. 

![Figure.3](images/drop_cols.png)

> Adding more nodes (Model_2):

The new model is designed as shown in the following image. The number of nodes increases without adding more layers. The training was slower and there were not much differences in the results.

![Figure 4.](images/model2_summary.png)

> Adding more layers:

Here we modify the first design by adding more layers.Model and results shown in the following.

![Figure 5.](images/model3_summary.png)

> Adding more layers and changing activation to ‘tanh’:

![Figure 6.](images/model4_summary.png)

> Adding more layers to Model_5:

![Figure 7.](images/model5_summary.png)

Following images show the training accuracy and training loss for the different models explained above.
From the graph, Model_5 shows a slightly better accuracy and loss compared to other models. In all models, there are a lot of fluctuations in the accuracy curve. The curve seems to improve very slowly. We tried different numbers for epochs and batch_size which did not make a big differences on the results and evaluation (under 1% improvement)   

![Figure 8.](images/accuracy.png)

![Figure 9.](images/loss.png)

Conclusions
We create a NN model to predict if a funded organization will be successful based on some organization’s features in the dataset. We created a base model and then try to optimize it by tuning the network. 

