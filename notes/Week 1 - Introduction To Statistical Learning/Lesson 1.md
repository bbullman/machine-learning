* Artificial Intelligence
	* Machines capable of mimicking human behavior
* Machine Learning
	* Machines capable of learning from experience
* Data Science
	* Business application of ML, AI, and other quantitative fields like statistics

![Machine Learning and Overlapping Fields](../lesson1_aimlds_overlap.png "AI-ML-DS-Overlap")
## Machine Learning

**What is Machine Learning?** A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P if its performance on T, as measured  by P improves the experience E.

**Ex:** Spam Filter

* Email is spam or ham? (Task T)
* Processing emails for spam or ham (Experience E)
* Percentage of emails correctly classified as spam or ham (Performance P)

**As we see more examples, our ability to classify them improves.**

* ML Model Training
	* Training Datasets are fed to a Machine Learning Algorithm to build a Prediction Model.
* ML Model Serving
	* Query Instances into the Prediction Model to return a Prediction
	
Prediction cannot be pushed back into the model without validation otherwise it would be a self-fulfilling prophecy.

**When to use AI/ML types?**

![When to use AI/ML modeling](../img/lesson1_when_use_ml.png "When to use AI/ML")

----
## Supervised Learning

Learn to predict an output from input using a **labeled** dataset.

* Linear/logistic regression
* K Nearest-Neighbors (First Assignment)
* Decision Tree
* Random Forest
* Gradient Boosting Trees
* Support Vector Machines
* (Deep) Neural Networks
* Others...

Labeling is EXPENSIVE. Oftentimes these are predictive models defined by the input labeled data. Predicting the target based on input.

**Ex:** Predict Delivery Times for UberEats, Product Recommendations on Amazon, Housing Prices on Redfin or Zillow

**Terminology**
* Label
	* The outcome we are interested in predicting
	* Ex: House Prices, cat images, loan defaults
* Features
	* An input/transformed variable that is used to predict a label
	* Number of bedrooms, colors in pixels, monthly income
* Training
	* Using labeled data to iteratively learn the function that transofrms an input into output
* Inference
	* Using a trained model to make predictions on new data (unseen data)
* Performance
	* Mean Square Error, Precisions Recall, AUC

----
## Unsupervised Learning

Find patterns and structure in an **unlabeled** dataset
* K-Means/KMedoids
* Hierarchical Clustering
* Gaussian Mixture Models
* Principal Component Analysis
* Anomaly Detection
* Autoencoders
* Others...

Often these are segmenting/classification problems or finding the input. No visibility into the target. **Cluster analysis** is a common way to do this.

**Ex:** Grouping by advertising group, Geographical clusters, grouping neighborhoods or houses...

**Terminology**
* Regression: Quantitative problems.
	* Predicting continuous value
	* House prices in Seattle?
	* Stock Prices
* Classification: Qualitative problems.
	* Predicting Discrete values
	* Will this applicant default on a loan?
	* Is this image a cat, dog, scorpion, pigeon?



----
## Reinforcement Learning

Has rewards. Think about playing a game.

**Ex**: Playing Starcraft, Chess, Go, Magic...

----
## Performance Measures and Metrics

**Classification Performance Metrics**
* Error is when a record is assigned a class when it belongs to another class
* Type 1 Error: AKA False Negative
	* Positive class is assigned to a record when the true class is negative
* Type 2 Error: AKA False Negative
	* Negative class is assigned to a record when the true class is positive

**Confusion Matrix for Classification Metrics**
	* Accuracy
		* Ratio of correctly predicted observation to the total observation
		* (TP+TN)/(TP + FP + TN + FN)
	* Precision
		* Ratio of true positives over all true and false positives
		* TP/(TP+FP) -> True Positives over (TP+False Positives)
	* Recall
		* Ratio of true positives over the sum of true positives and false negatives
		* TP/(TP+FN)

Precision or Recall are more appropriate for problems with imbalanced classes.
* Use Precision when the cost of false positives is high
	* It is more important to be right about our true predictions
	* Anomaly detection system, early warning systems
* Use Recall when the cost of false negatives is high
	* It is more important to recall all possible records of the positive class
	* Clinical decisions usually aim for a high recall
	* Car manufacturing

Precision vs. Recall 
* Increase classification threshold increases precision, decreases recall
* Decrease classification threshold decreases precision, increases recall

**Good ML designs strike an acceptable balance between the two.**

Other Evaluation Measures
* F1 Score takes a harmonic mean of precision and recall
* ROC/AUC (ROC - Receiver Operating Curve) is a graph showing performance of a classification model at all classification thresholds
* AUC (Area under ROC Curve) measures the entire two dimensional area underneath the entire ROC curve (integral calculus) from (0,0) to (1,1).
	* Scale Invariance, classification threshold invariance
	* It is the probability that the model ranks a random positive example more highly than a negative one

## MSE vs. MAE

MSE (Mean Standard Error)
* When you want to avoid very large errors and still fit outliers somewhat reasonably
MAE (Mean Absolute Error)
* When you think the outliers are merely corrupted data and should be ignored

----
## Variance

* Variance refers to the amount the function calculated would change based on a difference in training data on that function.
* Ideally it should not change much between models, but high variance models do exist and result in large changes to f.
* More flexible models have higher variance.
## Bias

* Bias refers to the error that comes from approximating a real-life problem as there are too many variables to account for in most models (ex: linear models)
* More flexible methods result in less bias.

As a general rule, more flexible methods will increase variance and decrease bias. The relationship between bias, variance, and test MSE (Mean Standard Error) is given as the *bias-variance tradeoff*. Ideally bias and variance would be low.

* Undefitting is when the model is not able to obtain a sufficiently low training error and has high bias.
* Overfitting is when the gap between training error and test error is too large and has high variance.