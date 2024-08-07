Weak Learner: can make predictions slightly better than random guessing
* High bias, cannot solve hard problems
* Ex: Naive Bayes, Logreg, Decision Stumps

Strong Learner has arbitrarily small error rate:
* Strong learners are our goal for ML
* Ex: Random Forests, deep neural networks

## Ensembles

* Learn a set of classifiers to make an ensemble
* Combine predictions of multiple classifiers to produce final prediction
* Assume they are independent, a mistake from one does not depend on the other
* In reality they are not completely independent
* Majority Voting: the ensemble makes a wrong prediction if the majority of the classifiers predict the wrong prediction
* Multilayer Stacking Ensemble
	* This is a Neural Network
	* Different training mechanism than Neural Networks but the structure is very much the same

![[lesson5_multilayer_stacking_ensemble.png]]
## Ensemble Types

* Different algorithms
* Algorithms could have different choice for parameters
* Dataset with different features (subspace of data)
* Dataset could have different subspaces (e.g. bagging, boosting)

## Ensemble Values

* No Free Lunch
	* No single algorithm wins every time
* When combining multiple independent and diverse decisions each of which is at least more accurate than random guessing, random errors cancel each other out, correct decisions are reinforced

## Ensemble Combiners

* Voting
* Averaging (if predictions not 0, 1
* Weighted Averaging
	* Base weights on confidence in component
* Learning combiner
	* Stacking
	* Region Boosting
### Weak Learners

Idea: weight the data set based on how well we have predicted data points so far:
* data points predicted accurately = low weight
* data points mispredicted = high weight
Result: focuses components on portion of data space not well predicted
## Bagging

* Varies Dataset
* Each training set a boostsrap sample
	* Bootstrap: select set of examples with replacement from original sample
* Algorithm:
	* for k = 1 to # classifiers
		* train' = bootstrap sample of train set
		* create classifier using train' as training set
	* Combine classifications with simple voting

## Boosting

* Iterative procedure to adapatively change distribution of training data by focusing more on previously misclassified records
	* Initially, all N records are assigned equal weights
	* Unlike bagging, weights may change at the end of a boosting round
	* Records that are wrongly classified have their weights increased
	* Records that are classified correctly have their weights decreased

### Boosting: Adaboost (Adaptive Boost)

Input:
* Training set D containing N instances
* T rounds
* A classification learning scheme
Output:
* A composite model

### Boosting: Arcing

Sample data set like bagging but probability of data point being chosen is weighted like boosting
# Stacking

* Stacking is an ensemble learning method
* It uses a metalearning algorithm to learn how to best combine the predictions from two or more base algorithms

# Blending

* Ensemble method to combine predictions
* Blending is the same as Stacked Generalization
* Instead of using trivial functions (such as majority voting / averaging) to aggregate the predictions of all predictors in an ensemble, we train a model (aka blender) to perform this aggregation.  

