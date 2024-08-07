# Modeling & Data Preparation/Preprocessing

Where the majority of time gets spent.
## Data Preprocessing

Important step in data mining and machine learning. Includes:
* Data Cleaning
	* Fill missing values, smooth noisy data, remove outliers, resolve inconsistencies
* Data Integration
	* integrate with other sources (sales -> holidays, sports -> crime. etc.)
* Data Transformation
	* Normalize and aggregate
* Data Reduction
	* Reduce volume while keeping most of the information
* Feature Extraction

Output is the final training set. Requires experience and practice!

### Data Quality 

Important for quality models. Garbage in, garbage out:
* Accuracy
* Completeness
* Conformity
* Consistency
* Integrity
* Timeliness
### Missing Data

* Reduces statistical power of a test
* Can cause bias in the estimation of parameters
* Complicates later analysis

Types of missing Data:
* MCAR (Missing Completely At Random)
	* The probability that a variable value is missing does not depend on the observed data values nor on the missing data values
* MAR (Missing At Random)
	* The probability that a variable value is missing partly depends on other observed data, but does not depend on any of the values that are missing
* MNAR (Missing Not At Random)
	* The probability that a variable value is missing depends on the missing data values themselves
	
Handling Missing Data:
* Listwise Deletion
	* Removes all data for a case that has one or more missing values
	* Without MCAR it is biased
* Pairwise Deletion
	* Maximizes all data available by retaining data which is required for an analysis
* Variable Deletion
	* Discard varaible which is missing values
* Multiple Imputation
	* Create n sets of imputations for the missing values
	* Analyze with standard methods to fit the interest of the datset
	* Pool the results
* Single Imputation
	* Single value substitution (mean, median, worst case, best case)
	* Values dynamically from the dataset (nearest value for example)
	* Single value (mean especially) is usually a bad estimate

**Keep in mind some of the readings are all over the place and there's contradictions in many of the papers.**
* Lots of papers say to avoid deletion
* Usually start with single imputation then move to multiple imputation (ML, MI)


![[lesson4_missing_data_analysis.png]]


## Outliers

## Class Imbalance

* Collect more data
* Try resampling the dataset
* Generate synthetic samples (SMOTE)
* Change performance metric
* Use a different algorithm
* Use penalized models

## Exploratory Data Analysis

Used by scientists to analyze and investigate. Often the first step. Makes it easier to discover patterns and spot anomalies, etc. Enables preliminary selection of appropriate models. Complements inferential statistics.

### Univariate non-graphical EDA

* A simple tabulation of the frequency of each category is the best univariate non-graphical EDA for categorical data
* Continuous variables
	* Sample means, medians, etc. about the distribution
	* Central tendency
		* location of a distribution has to do with typical mean median mode values
	* Spread
		* How far away from center we are still likely to find data values
		* Skewness - measure of asymmetry
		* Kurtosis - measure of peakedness relative to a Gaussian shape
* Histograms
	* Show central tendency, spread, modality, shape and outliers
* Bosplots
	* Show robust measures of location and spread as well as providing info about symmetry and outliers
### Multivariate Non-graphical EDA

* Correlation and Covariance
* Positive vs. Negative Correlation
* Positive Covariance --> When one measurement is above the mean, the other will probably be above the mean
* Negative Covariance --> When one variable is above its mean, the other is below its mean
* Side by side box plots and scatterplots

### Summary EDA

* Perform appropriate EDA first
* Check for mistakes, learn about distributions, learn relationships between data
* EDA is not exact science
* Get better with practice and experience

## Data Transformation

* Data transformation processes transform raw variables into meaningful variables
* Feature Engineering
	* Feature Transformation
		* Transforming existing feature into one with a specific function
	* Feature Construction
		* turning raw data into informative features that hte algorithm can understand
	* Dimensionality Reduction
		* Reduce number of features, while preserving overall information content
* Encoding Categorial features
	* Categorical variables need to be transformed into numerical values for ML
	* One hot encoding scheme creates a binary column for each category
	* We can use OneHotEncoder for preprocessing.
	* Can quickly grow in size if variable takes on many unique values
	* Label Encoding
		* Encoding the targets or labels
			* Normalize labels such that they contain only values between 0 and n_classes-1
* Handling high cardinality
	* Supervised Ratio
	* Weight of Evidence
* 