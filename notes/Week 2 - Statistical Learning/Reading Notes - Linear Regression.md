## Linear Regression

Linear Regression is a useful tool for predicting a quantitative response. Linear Regression can answer the following:

1. Is there a relationship between variables?
2. How strong is the relationship if there is one?
3. Which categories of data are associated with the data?
4. How large are those associations?
5. How accurately can we use this to predict future data?
6. Is the relationship **linear**?
7. Is there synergy among the categories?

## Simple Linear Regression

***"Simple linear regression lives up to its name: it is a very straightforward simple linear regression approach for predicting a quantitative response Y on the basis of a single predictor variable X."*** - ISLP

~~~
y^=~ B^0 + B^1*xi # formula for linear regression
~~~

We want to find an **intercept** B^0 and **slope** B^1 such that the resulting line is as close as possible to the data points.

Then we can derive  ```

```
ei = yi-y^i // ith Residual
```

and

~~~
RSS = e1^2 + e2^2 + e3^2...+ en^2 // residual sum of squares
~~~

The true relationship model:

![[lesson2_unknownfunction.png]]


* Sample mean is a good way to approximate.
* Using sample means creates an average gradient in terms of bias across different data points or observations.
* It is **unbiased**.

**Q:** "A natural question is as follows: how accurate is the sample mean µˆ as an estimate of µ? How far of will that single estimate of µˆ be?"
**A:** "Roughly speaking, the standard error tells us the average amount that this estimate µˆ difers from the actual value of µ. Equation 3.7 also tells us how this deviation shrinks with n—the more observations we have, the smaller the standard error of µˆ"

* Standard Errors can be used to compute confidence intervals and hypothesis tests such as the null hypothesis (there is no correlation between data X and Y) and alternative hypothesis (there is some correlation between data X and Y).

* T-statistics measure the number of standard deviations away from B^1 is from 0, and we expect that we have a t-distribution with n-2 degrees of freedom. It has a bellshape.
* Consequently we calculate the p-value based on the likelikehoood of observing any number equal to |t| or larger in absolute value.
	* A small p-value means it is is unlikely to observe such a substantical association between the predictor and response.
	* Small p-value = there is an association between predictor and response and we reject the null hypothesis.
## Measuring Accuracy of Simple Linear Regression

So we have a correlation, so let's think about it:
* Residual Standard Error (RSE)
	* RSE is considered a measure of lack of fit of the model to the data.
		* Small RSE fits the model well
		* Large RSE does not fit the model well
	* RSE is not always a good measure since it is measured in units of Y
* Residual Sum of Squares (RSS)
* Total Sum of Squares (TSS)
	* Calculates R^2
	* TSS measures the total variance in response Y and can be thought of as the amount of variability inherent in the response before the regression is performed.
	* R^2 measures the proportion of variability in Y that can be explained using X.
	* R^2 close to 1 indiciates a large proportion of the variability in response is explained by regression.
	* R^2 close to 0 indicates the regression does not explain much of the variability which can be because the model is wrong or the error variance is high or both.

## Multiple Linear Regression

Multiple predictor variables and multiple regression lines.

## Important Questions for all Regressions

1. Is at least one of the predictors X1, X2,...,Xp useful in predicting the response? 
2. Do all the predictors help to explain Y , or is only a subset of the predictors useful? 
3. How well does the model ft the data? 
4. Given a set of predictor values, what response value should we predict, and how accurate is our prediction?

### Important Answers for all Regressions

1. Recall that in the simple linear regression setting, in order to determine whether there is a relationship between the response and the predictor we can simply check whether β1 = 0. In the multiple regression setting with p predictors, we need to ask whether all of the regression coefcients are zero, i.e. whether β1 = β2 = ··· = βp = 0.
2. As discussed in the previous section, the frst step in a multiple regression analysis is to compute the F-statistic and to examine the associated pvalue. If we conclude on the basis of that p-value that at least one of the predictors is related to the response, then it is natural to wonder which are the guilty ones!
	1. The task of determining which predictors are associated with the response, in order to ft a single model involving only those predictors, is referred to as variable selection.
3. Two of the most common numerical measures of model ft are the RSE and R2, the fraction of variance explained. These quantities are computed and interpreted in the same fashion as for simple linear regression
4. Use confidence intervals and prediction intervals.

### Other Information about Linear Regression

* The standard linear regression model provides interpretable results and works quite well on many real-world problems. However, it makes several highly restrictive assumptions that are often violated in practice. Two of the most important assumptions state that the relationship between the predictors and response are additive and linear.

When we ft a linear regression model to a particular data set, many problems may occur. Most common among these are the following: 

1. Non-linearity of the response-predictor relationships. 
2. Correlation of error terms. 
3. Non-constant variance of error terms. 
4. Outliers. 
5. High-leverage points. 
6. Collinearity.

* An important assumption of the linear regression model is that the error terms, e1, e2,..., en, are uncorrelated.
	* Error correlations tend to happen when we have time-series data. If they are correlated then we may see tracking, as in adjacent residuals may have similar values.
	* "As an extreme example, suppose we accidentally doubled our data, leading to observations and error terms identical in pairs. If we ignored this, our standard error calculations would be as if we had a sample of size 2n, when in fact we have only n samples. Our estimated parameters would be the same for the 2n samples as for the n samples, but the confdence intervals would be narrower by a factor of √2!" - ISLP
		* This means we have a much stronger confidence (erroneous)
* Another important assumption of the linear regression model is that the error terms have a constant variance,.
	* Non-constant variances in the errors is known as heteroscedasticity
		* Identified from the presence of a funnel shape in heteroscedasticity the residual plot
* Outliers 
	* Residual plots are useful for finding outliers
	* Studentized residuals are calculated by dividing the residual by its estimated standard error. If it exceeds 3 then its a possible outlier.
* High-Leverage points
	* Have an unusual value for xi (observation)
	* Can compute the leverage statistic
	* Best move is to just remove them
* Collinearity
	* Collinearity refers to the situation in which two or more predictor variables collinearity are closely related to one another.
	* The presence of collinearity can pose problems in the regression context, since it can be difcult to separate out the individual efects of collinear variables on the response.
	* Causes standard error to grow and the t-statistic to decline.
	
As a general rule, parametric methods will tend to outperform non-parametric approaches when there is a small number of observations per predictor.





