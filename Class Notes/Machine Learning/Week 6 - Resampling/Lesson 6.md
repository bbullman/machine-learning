
## Introduction Second Half of Course

![[ml_process_diagram.png]]
## Why Resampling?

Problem: Before we deploy our model, we do not have a true test set that can be used to evaluate how well the model generalizes.

Solution: Carve out a test set from your training set.

Tools that involve repeatedly drawing samples from a training set.
Refit a model of interest on each sample in order to get more info.

Useful for:
* Model Assessment: Estimate Test Error Rates
* Model selection: Estimate Model Flexibility

Downside: Computationally expensive

## Types of Resampling

* Cross Validation - Used to estimate the test error associated with a given statistical learning method in order to evaluate
* Prediction Error
* Training Error rate - how well does model fit the training data
	* Underestimates the test error if the model is complex
* Larger sample size, lower the generalization error

### Strategies

### Validation Set/Hold out set

* Involves randomly dividing the available observations into two parts (test set or hold out set is the second set)
* Model is fit on the training set, and fitted model is used to predict the responses for observations in the test set
* Test error rate is calculated
* Easy to implement

Issues with holdout set:
* Test error estimated by a single test set is highly variable
* it highly depends on the observations in the training set and test set
* Since training is completed on a smaller set of observations, some statistical models may fit poorly on this smaller set
* In this case validation set error rate may overestimate the best error for the model fit on the entire data

### LOOCV Leave-One-Out Cross Validation

* LOOCV involves splitting the set of observations into two parts
* A single observation is used for the validation set and the observations make up the training set
* Model is fit on the n-1 training observations and a prediction y^ is made for the excluded observation, using its value x1
* This provides an unbiased estimate of the true error

* Single observation will have a LOT of variability
* Cycle through observations and iteratively inclue each observation in the test set and measure the error

Other Drawbacks:
* Expensive to implement computationally since you have to fit each observation in the test set
* If you are doing linear or polynomial regression a simple adjustment works
	* Usually linear is just a basis, so not really great
### K-Fold Cross Validation using the LogReg Model

1. Split the data into sets of folds for the training set.
2. For each parameter combination, evaluate on the next fold. Then do the same thing. Fold would be like a single data point.
3. Chose the parameter combination with the best metrics.

Very slow.
5-fold is ok.
10-fold CV example is very close to the LOOCV, not as variable as Holdout.

## Which one to Use?

* Sweet spot is in the middle, K-fold for 5 or 10
* No significantly high bias or significantly high variance.

## Cross Validation for Classification

CV is useful for classificaiton where Y is qualitative.

CV works like described earlier, except we use misclassification error instead of MSE.

## Sampling

With replacement creates independent samples.
Without replacement creates dependent samples.

## Bootstrap Approach

Variations of the bootstrap approach. Bootstrapping lets us resample from the original dataset.

Instead of simulating from the original data-set we simulate from the distribution that was fitted from the original data set. Parametric Bootstrap.

Can sample with replacement from the residuals of a fitted model. There are also approaches for handling dependent data such as time-series data.

The boostrap can provide faulty inference in the following situations:
1. Too little data (one data point would be awful)
2. Dealing with heavy-tailed distributions
3. When the data is not IID

## Optimization

* Optimization is concerned with optimizing objective function finding the value of an argument that minimizes of maximizes the function
* Most optimization is accomplished via minimizing the negative of an objective function (e.g., minimize - f(x))
* In minimization problems the objective function is often referred to as a cost function or loss function or error function

* Optimization is very important for machine learning
	* The performance of optimization algorithms affect the model's training efficiency
* Most optimization problems in machine learning are nonconvex
	* Meaning the loss function is not a convex function
	* Still useful in solving problems in ML

## Differences between Optimization and ML

* Optimization is minimizing an objective function
	* Reduce training error for training example
* Optimization algorithms attempt to find the point of minimum empirical risk 
* ML attempts to find the Expected Risk, based on inimizing the error on a set of testing examples
	* Which may be at a different location than the minimum of the training examples
	* And may not be minimal in a formal sense
## Optimization Algorithms

First Order and Second Order algorithms. There's a bunch.