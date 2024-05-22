## Feature Engineering

Categorical Features
* Nearly always need some preprocessing
* Difficult to impute missing data
* Can generate very sparse data due to high cardinality
* Two types:
	- Ordinal Categorical Features
		- Label encoding
		- Ordinal encoding
	- Nominal Categorical Features
		- One Hot encoding
		- Dummy Encoding
		- Mean or Target Encoding
		- Frequency Encoding

Numerical Features
* Can be readily fed to ML algorithms and models
* Quantization or Binning
* Log Transformation
* Power Transforms : Generalization of the Log Transform
* Feature Scaling or Normalization
	* Min-Max Scaling
	* Standardization
	* L2 Normalization

Text Features
* Bag-of-Words
* Bag-of-n-Grams
* Filtering for Cleaner Features
	* Stopwords
	* Stemming
	* Parsing and Tokenization
	* TF-DF

Adding/Subtracting/Multiplying/Ratios are another way to normalize a set of features (think bedrooms/number of total rooms). 

Datetime Features
* Holidays
* Local time for users
* Relate to external events (stock market, external data, movements)

Custom Transformations
* Create a class and implement three methods: fit() (returning self), transform(), and fit_transform() (by simply adding TransformerMixin as a base class)

## Feature Selection

* Filtering
	* Subset Selection
* Wrapper Methods
	* Recursive Feature Elimination
	* Forward Feature Elimination
* Embedded Methods
	* Lasso Regularization

### Subset Selection

* Start with null model (no predictors)
* Forward Stepwise Selection
	* Null Model
	* Add the most significant variable for p-k models
	* Keep adding them or ruling them out in terms of significance
* Backward Stepwise Selection
	* Start with all predictors
	* Try all models for k-1 predictors
	* Pick the best one
* RFE (Recursive Feature Elimination)
	* Recursively remove attributes and build a model on what remains
	* Use the model accuracy to determine which features are best used to predict the outcome
	* Steps
		* Train the estimator on the initial set of features
		* Prune the least important features from the list of features
		* Recursively repeat the process on the pruned list until stopping criteria is reached
* Lasso Regression
	* Talk more about it in future
## Summary

Filter Methods
* Usually fast, intuitive, universal, often used as a pre-processing method
* Can easily discard relevant features accidentally
* often select for highly correlated features
Wrapping Methods
* Treat learner as a blackbox
* Focus on final metric
* Time consuming (forward selection, genetic algs)
Embedded Methods
* Might be fast
* Easy to incorporate as part of training for other learners
* Highly metric / learner specific

## Transformation Pipelines
* Cleaning
* Feature transformation
* Feature Engineering
* Feature Scaling

### Hyper Parameters
 * Used before the training process begins
 * Weights are learned during training process, but hyper params are set before training begins
 * Model Hyperparams
	 * Cannot be inferred while fitting training data because they refer to model selection
	 * Ex. number of layers of neural network
 * Algorithm Hyperparams
	 * Bear no influence on the performance of the model but affect speed and qulaity
	 * Ex. Learning rate of gradient descent
 * Do not use examples from the test set!
 * Validation set of examples that the training data does not observe
 * Training Set
	 * Used to learn parameters of the model (not to be confused with the larger training pool)
 * Validation Set
	 * Used to guide the selection of all hyperparameters
 * 80% training 20% validation

## Steps of Pipeline Workflow

1. Prelaunch phase
2. Present the solution
3. What worked, what did not, what assumptions were made (system limitations too)
4. Document everything
5. Create visualizations

### Launch, Monitor, Maintain

* Plug the data in and write tests
* Monitoring/telemetry
* Sample the system's predictions
* Evaluate system's input data quality
* 