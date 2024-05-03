# Classification

* Categorical
	* Think eye color, or neighborhood.
* Predicting a qualitative response is known as *Classifying*
* Some ways to reach:
	* Logistic Regression
	* Linear Discriminant Analysis
	* Quadratic Discriminant Analysis
	* Naive Bayes
	* K-Nearest Neighbors (KNN)
	
* The reason we don't use Linear Regression for classification often comes down to encoding the response to a number and we'd have to test the difference between the response results.
	* The relationship between the conditions is arbitrarily defined
	* This would result in a totally different relationship

"To summarize, there are at least two reasons not to perform classifica-
tion using a regression method: (a) a regression method cannot accommo-
date a qualitative response with more than two classes; (b) a regression
method will not provide meaningful estimates of Pr(Y |X), even with just
two classes." -ISLP

## Logistic Regression

To fit a model for logistic regression we need to get outputs between 0 and 1.
* We use the maximum likelihood method.
* Odds can take any value between 0 and infinity.
* By taking the logarithm of odds we can approximate the function.
* Like other models we need to estimate the B0 and B1 via the training data.
* In the 'Default' Dataset:

*"In other words, we try to find β̂0 and β̂1 such that plugging
these estimates into the model for p(X), given in (4.2), yields a number
close to one for all individuals who defaulted, and a number close to zero
for all individuals who did not."* - ISLP

* Z-statistic is the same as the T-Statistic in terms of its role in analyzing the logistic regression
	* Large Z-statistic serves as evidence against the null hypothesis.
* Balance coefficients would indicate an increase or decrease of log-odds based on 1-unit of additional balance.


## Multiple Logistic Regression

* Use multiple coefficient estimates to produce a probability prediction.
* Multiple predictors make for a better analysis in many cases
	* When there is correlation amongst the predictors we can get vastly different values.
## Multinomial Logistic Regression

* Extend the number of classes above 2

Why do we need another method, when we have logistic regression?
There are several reasons:
* When there is substantial separation between the two classes, the
parameter estimates for the logistic regression model are surprisingly
unstable. The methods that we consider in this section do not suffer
from this problem.
* If the distribution of the predictors X is approximately normal in
each of the classes and the sample size is small, then the approaches
in this section may be more accurate than logistic regression.
 * The methods in this section can be naturally extended to the case
of more than two response classes. (In the case of more than two
response classes, we can also use multinomial logistic regressio

* Posterior probability is the probability that the observation belongs to the Kth class

# Estimating fk(x)

## Linear Discriminant Analysis for P=1

* Assume the function is normal or Gaussian
* LDA (Linear Discriminant Analysis) approximates the Bayes classifier by plugging in estimates for (pi)k, u(k), and sd^2 into the function.
## Linear Discriminant Analysis for P>1
* In the case of multiple predictors we extend the LDA classifier from a multivariate gaussian/normal prediction.
* The multivariate Gaussian distribution assumes that each individual pre-
dictor follows a one-dimensional normal distribution, with some
correlation between each pair of predictors.

### Default Data Set (Again)

From ISLP:

* First of all, training error rates will usually be lower than test error
rates, which are the real quantity of interest. In other words, we
might expect this classifier to perform worse if we use it to predict
whether or not a new set of individuals will default. The reason is
that we specifically adjust the parameters of our model to do well on
the training data. The higher the ratio of parameters p to number
of samples n, the more we expect this overfitting to play a role. For
overfitting
these data we don’t expect this to be a problem, since p = 2 and
n = 10, 000.
* Second, since only 3.33 % of the individuals in the training sample
defaulted, a simple but useless classifier that always predicts that
an individual will not default, regardless of his or her credit card
balance and student status, will result in an error rate of 3.33 %. In
other words, the trivial null classifier will achieve an error rate that
null is only a bit higher than the LDA training set error rate.
In practice, a binary classifier such as this one can make two types of
errors: it can incorrectly assign an individual who defaults to the no default
category, or it can incorrectly assign an individual who does not default to
4 
The careful reader will notice that student status is qualitative — thus, the normality assumption made by LDA is clearly violated in this example! However, LDA is often remarkably robust to model violations, as this example shows. Naive Bayes, provides an alternative to LDA that does not assume normally distributed predictors.

It is often of interest to determine which of these two types of errors are being made.

* Sensitivity is the percent of true defaulters that are identified
* Specificity is hte percentage of non-defaulters that are correctly identified

ROC Curve
	* Receiver Operating Characteristics
	* Area under ROC-Curve = AUC

## Quadratic Determinant Analysis

Quadratic discriminant analysis (QDA) provides an alternative approach.
quadratic Like LDA, the QDA classifier results from assuming that the observations discriminant from each class are drawn from a Gaussian distribution, and plugging es- analysis estimates for the parameters into Bayes’ theorem in order to perform prediction. However, unlike LDA, QDA assumes that each class has its own covariance matrix.

### Bias-Variance Tradeoff between LDA and QDA

* When there are p predictors then estimating a covariance matrix requires estimating a bunch of parameters.
* QDA estimates a separate covariance for each classes.
* By assuming the K-classes share a common covariance matrix, the LDA model becomes linear which means there are Kp linear coefficients to estimate. Consequently LDA is much less flexible than QDA as a classifier and substantially has lower variance and thus higher bias.
	* Roughly speaking LDA is better for less training observations so reducing variance is crucial.
	* QDA is recommended if the training set is very large.
	
## Naive Bayes

* Instead of assuming functions fall into specific family of distributions like Gaussian normal, we instead make a single assumption:
	* Within the kth class, the p predictors are independent
		* In a p-dimensional function we have to consider the marginal distribution
			* That is the distribution of each predictor on its own
		* Joint distribution
			* That each predictor has an association to each other (different predictors are associated)
		* By making the assumption that we are all independent,we eliminate the need to worry about the association between the predictors by assuming there is none.
	* KDE is a smoothed version of a histogram.


## Comparison of Classification Models

* LDA is a special case of naive Bayes
* LDA assumes the features are normally distributed, with a common in class covariance matrix, and naive Bayes instead assumes 
* independence of the features
* Neither QDA or Naive Bayes is a special case of the other

When the true decision boundaries are linear, then
the LDA and logistic regression approaches will tend to perform well. When
the boundaries are moderately non-linear, QDA or naive Bayes may give
better results. Finally, for much more complicated decision boundaries, a
non-parametric approach such as KNN can be superior. But the level of
smoothness for a non-parametric approach must be chosen carefully. In the
next chapter we examine a number of approaches for choosing the correct
level of smoothness and, in general, for selecting the best overall method.

## Poisson Regression and Poisson Distribution

* Useful when non-linear and non-logistic
* Distribution is used for model counts
	* Take on nonnegative integer values
* Gaussian, Bernoulli and Poisson regressions are of the same **exponential** family.
	* Includes Gamma and Binomial as well.