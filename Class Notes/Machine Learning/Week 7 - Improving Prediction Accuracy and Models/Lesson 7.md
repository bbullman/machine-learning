# Improving Linear Models & Model Interpretability

* Shrinkage methods
* Ridge regression
* Lasso regression
* Comparison of Shrinkage methods

## Prediction Accuracy

Least squares estimates have low bias and low variance
* When the relationship between label and featurs is linear
* the numbero f observations n is much bigger than the number of predictors

### Problems 
* When N ~ P then the least squares fit can have high variance and may result in overfitting and poor performance of the test data.
* When N < P the variability of the least squares fit increases dramatically and the variance of these estimates is infinite

### Solution
 * Shrink or control the coefficient estimates to reduce the variance at the cost of some increase in bias

## Model Interpretability

* Not all features are associated with the label
* Leaving these variables leads to unnecessary complexity in the resulting model
* The model would be easier to interpret by removing the irrelevant variables
* Need an automated way to 'zero out' coefficients of these features

### Alternatives to Least Squares

* Subset selection (identify a subset of p predictors) - forward, backwards, recursive feature elimination.
* Shrinkage (embed methods) - fit a model involving all predictors but some of the coefficients are...
* Dimensionality Reduction

### Error Estimates

* Training MSE underestimates the test MSE.
* We can decrease training MSE or increase R^2 by including more variables in the model
* Training set RSS and training set R^2 cannot be used to select form among a set of models with different numbers of variable
* Need to adjust the training error for the model size being used!

### Adjusting Error Estimate for Tests

* Colin Mallow's selection Criterion for a model with 'd' predictors
* Akaike's Information Criterion (AIC)
* Bayesian Information Criterion (BIC)
* Adjusted R^2

BIC - Lower the number of features, small as possible

Estimating test error:
1. Directly
	1. Using either a validation set or cross validation approach (use when possible)
2. Indirectly
	1. Estimate test error by making predictions

Choosing one of the above is best.

## Shrinkage Methods

* Fit a model containing all p predictors using a technique that constrains or regularizes or shrinks the coefficient estimates
* The two best known techniques:
	* Ridge Regression
	* Lasso Regression
### Regularization

Any modification we make to a learning algorithm that is intended to reduce its generalization error but not its training error.

* Better description of the model
* Prevent the weights/learned parameters from becoming too large
* Smaller weights generate a simpler model and help avoid overfitting

As constrained optimization

* Minmize some loss fuction while limiting the model complexity (minimize Loss (data/model) such  that complexity (model) <= t.
* The regularized objective function is mentioned...

Subsquared of the coefficients needs to be close to 0 so we have the complexity.

....TODO: Missed a few slides.

...

![[lesson7_lasso_v_ridge.png]]

![[lesson7_lasso_v_ridge2.png]]

# Selecting Lambda

* How to pick a value for lambda
* Select a grid of potential values, use cross validation to estimate the error rate on test data for each value of lambda

Elastic Net Penalty
* A compromise between Ridge and Lasso
* The elastic-net selects variables like the lasso, and shrinks together the coefficients of correlated predictors like Ridge
* Considerable computational advantages over the Lq penalties
* 