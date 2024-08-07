
# Decision/Regression tree bagging

## Bagging

Bootstrap aggregation, or bagging, is a general-purpose procedure for reducing the variance of a machine learning method by combining the result of multiple classifiers trained on different sub-samples of the same data set.

Bagging:
1. Create bootstrap samples (sample with replacement).
2. Train separate classifier on each sample. 
3. Classify new data point by majority vote or average.

Sample with replacement! Not all observations are used.

No coss validation.

# Random forest regression/classification

Random forests are ensemble of multiple independently trained decision trees
* Each tree is trained using a sample of observations and a sample of independent variables 
* Think about three doctors diagnosing heart disease. 
	* One doctor is trained by just looking at ECG, one doctor is a Chinese medicine doctor who is trained only by only touching the pulse, and one doctor is trained by looking at the ultrasound image 
	* Each doctor is trained on data of different patients (there might be overlapping among the sets of patients)

Pros:
* Better performance than regular trees
* Automatic feature selection
* Less risk of overfitting
* Can be parallelized easily
Cons:
* Less interpretability
* In some algorithms data is copied so higher performance overhead (memory, etc.)

### Errors

Review: 
* BIAS + VARIANCE + NOISE
* Bias: the difference between the predicted and actual values
* Variance:: the variability of a model predictor for a given data point

Bagging reduces variance by averaging the predictions from multiple classifiers. Bagging does not do much for Bias.
# Gradient boosting regression/classification

Boosting averages and reduces both bias and variance.

* Learn classifiers in sequence: later classifiers focus on examples that were misclassified by earlier classifiers. 
* Weighted voting: weight the predictions of the classifiers according their prediction accuracy.

Weight each iteration based on how it was incorrectly classified on previous classifiers.

Too many outliers is bad for performance and can make classification methods worse.

Adaboost: redistribute the weights in the data so that later classifier focuses more on the misclassified examples by previous classifiers.

Gradient boosting:
1. Calculate the residual for all examples in the training data (the difference between the outcome of the first learner and the real value). 
2. Build learner to predict/fit the residual left from the previous classifiers.
3. These two steps continues until certain threshold is met.

### XGBoost

* Additive tree model. Add new tress to compliment existing trees
* Response is the optimal linear combination of all trees
* Huge for Kaggle competitions (over 50% of winning submissions use XGBoost)

### Summary

Boosting Pros:

1. Often best off-the-shelf accuracy
2. Using model for prediction requires only modest memory and is fast
3. Does not require careful normalization of features to perform well
4. Like decision trees, handles a mixture of feature types

Cons:

1. Interpretability
2. Careful tuning of learning rate
3. Not easy to parallel like RF since each classifier needs to be trained in sequence

Bagging:

1. Resamples data points
2. Weight of each classifier is the same
3. Only reduces variance
4. No CV
5. Replacement

Boosting
1. Reweights data points
2. Weight is dependent on other classifiers
3. Both bias and variance are reduced