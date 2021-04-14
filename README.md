# Optimizing an ML Pipeline in Azure

## Overview
This project is part of the Udacity Azure ML Nanodegree.
In this project, we build and optimize an Azure ML pipeline using the Python SDK and a provided Scikit-learn model.
This model is then compared to an Azure AutoML run.

## Summary
**In 1-2 sentences, explain the problem statement: e.g "This dataset contains data about... we seek to predict..."**
We were given a dataset of Bank Marketing with the primary task of carrying out binary classification on the target.


**In 1-2 sentences, explain the solution: e.g. "The best performing model was a ..."**
The best performing model was an auto ml voting model with an accuracy of 0.91642, beating out the sklearn logisitic regression model with an accuracy of 0.907


## Scikit-learn Pipeline
**Explain the pipeline architecture, including data, hyperparameter tuning, and classification algorithm.**
We load data from csv, and in our training script apply a LogisticRegression instance from sklearn as our classification algorithm.  We use a Random Parameter sampling to search a space of regressions hyperparameters for Regularization Strength and Max Iterations. We optimized for Accuracy. We applied a bandit policy for early stopping.

**What are the benefits of the parameter sampler you chose?**
It supports early stopping of low performance runs. 


**What are the benefits of the early stopping policy you chose?**
We can save computation using Bandit Policy that allows termination if run is not better than best run at interval n within a "slack" +/- range.

## AutoML
**In 1-2 sentences, describe the model and hyperparameters generated by AutoML.**
AutoML created a Voting Ensemble where each model was weighted and their combined outputs computed together. The ensemble was made up of differentially weighted instances of LightGBM and LogisiticRegression.

## Pipeline comparison
**Compare the two models and their performance. What are the differences in accuracy? In architecture? If there was a difference, why do you think there was one?**
The AutoML had about ~ 0.01 better accuaracy. THe main difference appears to be training one model with hyperdrive and multiple models via automl.

## Future work
**What are some areas of improvement for future experiments? Why might these improvements help the model?**
We can try either different models and different parameter sampling for the hyperdrive experiment.  The parameter sampling was conservative, so not clear we could not due better given more computation.  For example we can use Grid sampling which will exhaustively examine the search space, or we can try Bayesain which will pick samples based on previous runs improvements to make further improvements.

## Proof of cluster clean up
**If you did not delete your compute cluster in the code, please complete this section. Otherwise, delete this section.**
![]https://github.com/DAWHEEL/Optimizing_ML_Pipeline/blob/main/Delete.jpg)