# Classification

Input data: Feature vector X and a qualitative response Y taking values in the set C

Task: Build a function f(X) that takes as input the feature vector X and predicts value for Y

Classification algorithms estimate the probabilities that X belongs to each category in C.

Linear Regression doesn't work because it implies a numbering of response variables. With the binary response variable the Y value might lie without 0 and 1 and that is also impossible since the statistical probability needs to be between 0 and 1.

The real problem is bounding the models. Hence why we use Logistic Regression and similar instead of Linear for problems of classification.

## Logistic Regression


Bernoulli Random Variable takes on vlaues 1 and 0 with probability p and (1-p) respectively. The binary response can be modeled as such.

* Expectation of a Bernoulli random variable is p
* Variance of a Bernoulli Random variable is p(1-p)

### Maximum Likelihood Estimation

The conditional likelihood with the assumption that the observations are independent is a large Pi function.

The likelihood function does not have a closed form solution. We use optimization methods to find the optimal values for the coefficients based on the error. Once they converge hitting a minimum they've reached that equilibrium.

Matrix inversion can go wrong so in the exercise, Hessian matrix to the ^-1 it becomes extremely slow. GPUs can do it really fast which is why we use them for machine learning. Hessian matrix gets larger with more features, and can be a sparse matrix, and might have issues with inversion otherwise.

MLE provides an estimate of the intercept and slope parameters.

## Bayes

## LDA 

* Make an assumption about the distribution ahead of time: is it Gaussian, Poisson?
* Estimates for the regression coefficients are surprisingly unstable when the classes are well separated
* If 'n' is small and the distribution of predictors is approximately Gaussian, the linear discriminant model is more stable
* Linear Discriminant Analysis (LDA) is popular when we have more than two classes
* Linear.

Assume Gaussian, assume p = 1. Plug it into Bayes Theorem.

For p>1 it's the case of multivariate Gaussian dstribution.
* Still linear.

### LDA vs. QDA

**LDA**: Assume that X= (X1...Xp) is drawn from a multivariate gaussian distribution, with a class-specific multivariate mean vector and a **common** covariance matrix.

**QDA**: Assume that X=(X1...Xp) is drawn from a multivariate Gaussian distribution, with a class-specific multivariate mean vector and a **class-specific** covariance matrix.

* Called QDA because the X term is squared (vector form) essentially
![[lesson3_lda_vs_qda.png]]

## Logistic Regression vs. LDA

![[lesson3_logistic_regr_vs_lda.png]]

## QDA vs. Logistic Regression and KNN

![[lesson3_qda_vs_logregr_knn.png]]