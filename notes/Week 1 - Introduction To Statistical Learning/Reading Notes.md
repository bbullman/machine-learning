Covers the Chapter 1: Introduction and Chapter 2: Statistical Learning.

## Chapter 1: Introduction 

* **Supervised Learning** refers to building a statistical model for predicting, or estimating an output based on inputs.
* **Unsupervised Learning** refers to building a statistical model with input without a supervised output.
* **Least Squares** principle became Linear Regression modeling.
* The Python3/pip package is called ISLP

## Chapter 2: Statistical Learning

* Input or Independent Variables are also known as predictors and are often represented as **X** in equations with subscript distinguishing between them.
* Dependent or Response Variables are often represented by Y and a fixed function of X such that *Y = f(X) + e* where e is denoted as an error term.
* Error term *e* always has approximate mean zero.

### Estimating function f

* Prediction
	* In Predictive modeling f is often a black box if Y^ is considered to yield accurate results
	* Accuracy of Y^ as a prediction for Y^ depends on the **reducible error** and the **irreducible error.**
	* The variability associated with *e* also affects the accuracy of our predictions, known as the irreducible error because no matter how well we estimate f, we cannot reduce the error introduced by *e*.
	* The first part of the function *Y = f(x) + e* in the predictive case of E(Y - Y^)^2 and is the **reducible error** and the **expected value**, and the var(*e*) represents the **variance** and **irreducible error**.
	* **Ex:** Patient having adverse reaction to a drug based on many factors. Some errors cannot be accounted for such as manufacturing quality on a given day or patients chemical imbalances on a given day.
* Inference
	* We use inference to find *f* and we cannot treat f^ as a black box.
	* It is the inverse: which predictors are associated with the response, the relationship of the response with each predictor, and the relationship between the ouptu and each predictor adequately summarized by an equation (linear) or more complex maths?
* Both Predictive and Inferred Modeling
	* The real estate market example: schools, taxes, zoning, crime rates, etc.
		* Inference example.
	* Is the house over or under-valued, how much extra would it be worth if it had the view of a river.
		* Predictive example.
* **Linear models** allow for simple and interpretable for inference but may not be as good at prediction. 
* Less linear models might be better at predicting an outcome but are less interpretable for inference.
* **Training Data** is the name by which we give our dataset (observations, data points)
* **Model** or Method is what we apply to the Training Data to estimate ***f***
* Most models can be characterized as parametric or non-parametric
* **Parametric Models**
	* Two-step model-based approach
		1. Make an assumption about the functional form or shape of f
			1. Ex: It's linear
		2. Make a procedure that uses the training data to fit or train the model
			1. Ex: Least Squares
1. **Non-Parametric Models**
	1. Do not make any assumptions about the functional form of ***f***
		1. They move as close to the data points as possible
		2. Thin-Plate Spline is one method
* More difficult models are harder to interpret, as it is difficult to map the predictors to any response
### Examples of Models
From least flexible but most interpretable to most flexible and least interpretable:
1. Subset Selection Lasso or Lassos in general
2. Least Squares
3. Generalized Additive Models
4. Trees
5. Bagging, Boosting
6. Support Vector Machines
7. Deep Learning
8. Others...
Over fitting is when one model is too flexible and molds to the data too cleanly without giving an appropriate measure of ***f***.

