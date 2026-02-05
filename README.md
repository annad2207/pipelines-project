
# Fashion Forward Forecasting

Building a machine learning model that will predict whether a customer __will__ leave a positive review (1) for a clothing item they are reviewing or __not__ (0). This brings value to the business as it allows for enhanced customer insights, as well as being able to focus marketing for products deemed popular. Having these insights offers the company a strategic advantage for understanding the opinions of their customers, which is why it is important to have a high performing model to predict this. 

## Getting Started

The notebook containing all stages of the model pipeline development, from EDA to evaluation can be found at the path pipelines-project/starter/Pipeline_notebook.ipynb.  

### Dependencies

Please see the updated requirements.txt file for the dependencies. 


# Project Overview

This project followed several key steps in the machine learning lifecycle and this can be followed in the notebook with clear headings. 
 * EDA
 * Feature Engineering Pipeline Build 
 * Combining to make a training pipeline 
 * Fitting the results
 * Fine tuning the results 
 * Hyperparameter tuning 
 * Model evaluation 
 * Model interpreatation (Will take place in the README rather than notebook)
 
 
The complete process of getting to the final model and the subsequent commentary can be found in the notebook. 

## EDA
 To give a brief summary, EDA was conducted as a univariate and multivariate level, as well as categorising the features into their respective categories and removing Customer ID and review title for being redundant. 
 
The final feature split was: 
__Numerical__
`Age`
`Positive Feedback Count`

__Categorical__
`Division`
`Department`
`Class name`
__Text__
`Review text`

## Pre Processing
Numeric -> `MinMaxScaler`
Categorical -> `OneHotEncoder`
Text-> `Tfidf`

## Training Pipeline

Base model- `RandomForestClassifier`

## Fine Tuning 
* `Logistic Regression`
* `GradientBoostingClassifier`
* `SVC`

## Hyperparameter Tuning
* classifier__C
* classifier__penalty
* classifier__solver

 ## Model Interpretation 
 The final model iteration is as follows: 
 
 
 __Best Logistic Regression Pipeline Model:__ 
 
 
              precision    recall  f1-score   support

           0       0.71      0.60      0.65       349
           1       0.91      0.94      0.93      1496

    accuracy                           0.88      1845
   macro avg       0.81      0.77      0.79      1845
weighted avg       0.87      0.88      0.88      1845
 
 After using GridSearchCV, it was determined that this logistic regression model was the best at predicting whether a review would be positive and the product would be reccomended, or not. The challemges that were faced throughout the project (an imbalanced target feature and wanting to avoid model bias as much as possible) are still somewhat present in the final iteration, although have certainly been mitigated as far as possible without adopting any resampling approaches that were out of scope for this project. 
 
 
 With the final model iteration, we can interpret the findings to show what this would actually mean if this model were to be productionised and performed on an inference dataset to predict reviews without a reccomendation label. 
 
 The model correctly predicts the reccomendation outcome of reviews __88%__ of the time. This high accuracy indicates reliable performance in general, providing confidence that the model’s predictions can support business decisions related to customer sentiment analysis.
 
 The model is particularly good at recognising positive feedback (__0.91__ precision and __0.93__ recall). This reliability allows confident use of the model to identify satisfied customers, supporting targeted marketing and customer retention strategies.

However, the model is not as strong at detecting not reccomended reviews, with recall of only __60%__. This means the business might miss about 40% of not reccomended reviews if relying solely on this model. 

If this model were to go in to production, business stakehokders should be made aware of the class imbalance and the implications this may have, and developers could be given more time and resources to try and overcome this issue further, but overall this is a model with sound performance and can offer strong strategic insights. 