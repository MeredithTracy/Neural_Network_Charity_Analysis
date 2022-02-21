# Neural Network Charity Analysis

## Overview
The purpose for this analysis was to assist the client in making a neural network to help create a binary classifier that is capable of predicting whether applicants will be successful if they are funded by Alphabet Soup. 

To achieve this, I will first preprocess the data to create my model. Then compile, train, and evaluate my model. Finally, I will try to optimize my model to create more accurate results. 

## Results
### Data Preprocessing
The data I was provided had 34,000 organizations that received funding from Alphabet Soup. I first need to clean up the data in order to create the learning model. 

The columns included: 
- EIN and NAME—Identification columns *
- APPLICATION_TYPE—Alphabet Soup application type *
- AFFILIATION—Affiliated sector of industry
- CLASSIFICATION—Government organization classification *
- USE_CASE—Use case for funding
- ORGANIZATION—Organization type
- STATUS—Active status
- INCOME_AMT—Income classification
- SPECIAL_CONSIDERATIONS—Special consideration for application
- ASK_AMT—Funding amount requested
- IS_SUCCESSFUL—Was the money used effectively *

I first dropped the identification columns (EIN and NAME) as I do not need them for the model. The IS_SUCCESSFUL column is the target since it has the binary data on if the funding was used effectively. I then binned the columns that had a large number of unique responses (CLASSIFICATION and APPLICATION TYPE). I finally encoded the categorical data and merged it to the full dataset to make it ready to create the model. 


### Compiling, Training, and Evaluating the Model
**My original model consisted of:**
- binned columns: APPLICATION_TYPE and CLASSIFICATION
- 2 hidden layers
    - relu, 80 neurons
    - relu, 30 neurons
- output layer was sigmoid
- 100 epochs, callback every 5 epochs
![Original_model](https://github.com/MeredithTracy/Neural_Network_Charity_Analysis/blob/main/Images/Original_model.png)


**My first attempt of optimization consisted of:**
- Adding the ASK_AMT column to our binning list before encoding our dataset.
- 2 hidden layers
    - relu, 80 neurons
    - relu, 30 neurons
- output layer was sigmoid
- 100 epochs, callback every 5 epochs
I added a new binning column to try and focus the model a bit better. The ASK_AMT column had 8747 unique values so narrowing that could be helpful. 

![Attempt1](https://github.com/MeredithTracy/Neural_Network_Charity_Analysis/blob/main/Images/Attempt1.png)


**My second attempt of optimization consisted of:**
- binned columns: APPLICATION_TYPE, CLASSIFICATION, ASK_AMT
- 3 hidden layers
    - relu, 100 neurons
    - relu, 50 neurons
    - relu, 25 neurons
- output layer was sigmoid
- 100 epochs, callback every 5 epochs
For my second attempt, I kept my new binned column and added a new hidden layer and adjusted the neurons. I kept my activation functions the same for this round. 

![Attempt2](https://github.com/MeredithTracy/Neural_Network_Charity_Analysis/blob/main/Images/Attempt2.png)


**My third attempt of optimization consisted of:**
- binned columns: APPLICATION_TYPE, CLASSIFICATION, ASK_AMT
- 2 hidden layers
    - relu, 100 neurons
    - tanh, 50 neurons
- output layer was sigmoid
- 100 epochs, callback every 5 epochs
For my third attempt, I kept the binned columns and returned to two hidden layers. I did change the neurons and changed one of the input activation functions to a tanh. 

![Attempt3](https://github.com/MeredithTracy/Neural_Network_Charity_Analysis/blob/main/Images/Attempt3.png)


**My fourth attempt of optimization consisted of:**
- binned columns: APPLICATION_TYPE, CLASSIFICATION, ASK_AMT
- 4 hidden layers
    - relu, 100 neurons
    - relu, 80 neurons
    - relu, 60 neurons
    - relu, 40 neurons
- output layer was sigmoid
- 100 epochs, callback every 5 epochs
For my final attempt, I decided to change up a couple things to see if it changed anything. My three previous attempts all resulted in very similar results so I wanted to change a couple things with this section. We added two more hidden layers and adjusted the neurons. Every layer was relu for this round since it seemed to have slightly better results compared to the tanh attempt. 

![Attempt4](https://github.com/MeredithTracy/Neural_Network_Charity_Analysis/blob/main/Images/Attempt4.png)


## Summary
Unfortunately, I was unable to create a model with 75% accuracy or higher. My first attempt at optimization had the best results out of the four but only by a fraction of a percent. I believe that a supervised model could potentially serve this data better since we are looking at a binary data target. 
