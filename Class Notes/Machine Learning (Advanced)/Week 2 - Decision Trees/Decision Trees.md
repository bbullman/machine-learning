
Ideally do not implement them manually. Structure of the decision tree depends on the training data and hyperparameters.

![[lesson2_decisiontrees.png]]

* Do not need a node for every feature
* it's possible if you do use every feature you may overfit
* The tree algorithm stopping criteria will exclude features based on importance or number of data points, leaves, hyperparameters.
* For simplicity's sake let's assume these are binary
	* Usually these are used in a binary scenario

## Types of Decision Trees

* Categorical Variable Decision Tree
	* Categorical target variable
* Continuous Variable Decision Tree
	* Continuous target variable

### Pros and Cons

* Tree based methods are simple and useful for interpreation
* Tend to overfit leading to poor performanc
* Discuss bagging, random forests, and boosting in the futur
* Combining multiple trees to often yield improvements in prediction accuracy at the expense of some loss interpretation

## Algorithms

* Hunt's Algorithm
* SLIQ
* Two other common ones

## Hunt's Algorithm

1. Let Dt be the set of training records that reach node t.
2. Procedure
	1. If Dt contains records that belong to the same class as yt, then t is a leaf node labeled as yt
	2. If Dt contains an empty set, then t is a leaf node labeled by the default class, yd
	3. If Dt contains records that belong to more than one class, use an attribute test to split the data into smaller subsets. Recursively apply the procedure to each subset.

## Decision Tree Training

* Greedy strategy
	* Split records based on an attribute test that optimizes certain criterion
* Issues
	* Determine how to split the records
	* What defines a good split?

### Splitting Variables

* Multi-way split
	* Split on categorical variables
* Binary split
	* Group categorical variables into binary groups

### Splitting Continuous Variables

* Discretization to form an ordinal categorical attribute
	* Static - do it once at the start
	* Dynamic - ranges can be found by equal interview, or bucketing percentiles or clustering
* Binary Decisions or Multi-way split

**Note: Binning (buckets) can be really important to get good information

## Tree Algorithm Splitting

Four common algorithms choose when to split:
1. Gini impurity. Higher value = higher impurity.
	1. Categorical target success/failure
	2. higher value of gini means higher the homogeneity
	3. CART (classification and regression tree) uses gini method to create binary splits
2. Chi-Square
	1. Works with categorical target variable success or failure
	2. It can perform two or more splits
	3. CHAID tree
3. Make one from scratch
	1. Choose an attribute (rain or no rain)
	2. Split data using chosen attribute into disjoint sets
	3. Recursive partitioning for each subset
Information Gain:
* How much information is retained when we do the split?
* Less impure node requires less information to describe it
Entropy
* Measures level of impurity in a group of examples for classification problems

# Constraints

Always prefer the simpler model if they give the same results.

Minimum samples for a node split is used to control over-fitting. Higher values prevent a model from learning relations which might be highly specific. Too high values can lead to underfitting.

Similar to leaf nodes - used to control overfitting and maximum depth of tree (vertical tree depth).

Tree Pruning is important but you have less control in pruning than you do with the validation set.