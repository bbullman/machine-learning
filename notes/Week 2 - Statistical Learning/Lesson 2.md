## Maximum Likelihood Estimation (MLE)

Supposed that the random variables X1...Xn form a random sample distribution f(x|theta); if X is continuous random variable, f(x|theta) is pdf, if X is discrete random variable f(x|theta) is point mass function.

If observations are independent then we can translate it based on probability theory. It becomes the likelihood function.

## Simple Linear Regression

Linear Regression is trying to fit the data to a linear model.

Y ~ B0 +B1X // ~ means "approximately modeled as"
* Remember: 100% accuracy means you're doing something wrong
  
We estimate the coefficients here:
* y^ = B^0, + B^1x // x is the estimated value
By fitting this equation to the model
* Y=B0+B1X+e // e is the error

We are given (x1,y1),(x2,y2)...(xn,yn) and estimate a linear function to fit the data. We can make it complex as we progress.

### Minimizing Residuals

Residual is the difference between actual and predicted value
Residual for the ith observation is given by ei = yi -- y^i

## Estimated Coefficients

![[lesson2_simple_linear_regression.png]]


**P-Value:** The more generic version of that equation (in other parts of statistics) is (value - mean)/(standard deviation)

## Multiple Linear Regression

![[lesson2_rss_overstated.png]]
![[lesson2_outlier_example.png]]

Newspaper has no value in the regression analysis here.

## Duplicating Data

Say you accidentally duplicate your data in the input.

What happens?
* Covariance decreases - your data is a placebo and you become more confident in your result.
* Coefficients don't change.

## Normalizing

Nrmalizing is best to compare all values. It is like comparing apples to apples rather than apples to oranges. Recommendation to normalize whenever the values are on different scales.