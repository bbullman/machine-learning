1. Use normalization as part of the modeling process: min max normalization.
2. Use normalization as part of the modeling process: centering and scaling.
3. Use analysis of variance to compare the performance of a pair of models.
4. Use hold-out validation to compare the performance of a pair of models using a large data set.
5. Normalize data.

## EDA (Exploratory Data Analysis)

* Classical DA
	* Problem => Data => Model => Analysis => Conclusions
* Exploratory (EDA)
	* Problem => Data => Analysis => Model => Conclusions
* Bayesian
	* Problem => Data => Model => Prior Distribution => Analysis => Conclusions



|   |
|---|
|A summary analysis is simply a numeric reduction of a historical data set. It is quite passive. Its focus is in the past. Quite commonly, its purpose is to simply arrive at a few key statistics (for example, mean and standard deviation) which may then either replace the data set or be added to the data set in the form of a summary table.|
EDA uses the data as a "window" to peer into the heart of the process that generated the data. There is an archival role in the research and manufacturing world for summary statistics, but there is an enormously larger role for the EDA approach.

## Identification of Outliers

Identification of potential outliers is important for the following reasons.

1. An outlier may indicate bad data. For example, the data may have been coded incorrectly or an experiment may not have been run correctly. If it can be determined that an outlying point is in fact erroneous, then the outlying value should be deleted from the analysis (or corrected if possible).
    
2. In some cases, it may not be possible to determine if an outlying point is bad data. Outliers may be due to random variation or may indicate something scientifically interesting. In any event, we typically do not want to simply delete the outlying observation. However, if the data contains significant outliers, we may need to consider the use of robust statistical techniques.

Outlier Labeling, Accomodation via the model, or identification (actually calculating it's an outlier) is important.

1. Normality Assumption (assuming the distribution is normal)
2. Single versus multiple others
	1. Some tests are made for single OR multiple outliers
3. Masking and Swamping
	1. Masking can occur when we specify too few outliers in the test. For example, if we are testing for a single outlier when there are in fact two (or more) outliers, these additional outliers may influence the value of the test statistic enough so that no points are declared as outliers.
	2. On the other hand, swamping can occur when we specify too many outliers in the test. For example, if we are testing for two or more outliers when there is in fact only a single outlier, both points may be declared outliers (many tests will declare either all or none of the tested points as outliers).
		1. Also, masking is one reason that trying to apply a single outlier test sequentially can fail.
4. Z-Scores
	1. The Z-score of an observation is defined via an equation Zi = (lookup), with 𝑌¯ and **_s_** denoting the sample mean and sample standard deviation, respectively. In other words, data is given in units of how many standard deviations it is from the mean.
	2. Although it is common practice to use Z-scores to identify possible outliers, this can be misleading (particularly for small sample sizes)
	3. Modified Z-scoe (MAD) uses the median absolute deviation
5. Formal Outlier Tests
	1. Grubbs Test (single dataset), Tietien-Moore Test (generalization of the Grubbs' test) for more outliers, Generalized Extreme Studentized Deviate (ESD) test. Requires only  an upper bound on the suspected number of outliers and is the recommended test when you do not know the number of outliers.
6. Lognormal Distribution
	1. The tests discussed here are specifically based on the asumption that the data follows a normal distribution. Transform the data to normal if it follows a different.

## Preprocessing Data

* Data cleaning
	* Handle missing data, smooth noisy data, identify or remove outliers, and resolve inconsistencies
* Data integration
	* Integration of multiple databases, data cubes, or files
* Data reduction
	* Dimensionality reduction 
	* Numerosity reduction 
	* Data compression 
* Data transformation and data discretization 
	* Normalization 
	* 6Concept hierarchy generation

## Missing Data

The term missing data is defined here as a statistical problem characterized by an incomplete data matrix that results when one or more individuals in a sampling frame do not respond to one or more survey items.

Three Mechanisms of Missing Data: Random Missingness (MCAR) and Systematic Missingness (MAR and MNAR)

Data can be missing randomly or systematically. According to Rubin’s (1976) typology, there are three missing data mechanisms (Little and Rubin, 1987; Schafer & Graham, 2002):

* MCAR (missing completely at random)– the probability that a variable value is missing does not depend on the observed data values nor on the missing data values. The missingness pattern results from a process completely unrelated to the variables in one’s analyses, or from a completely random process (similar to flipping a coin or rolling a die).

* MAR (‘‘missing at random’’)– the probability that a variable value is missing partly depends on other data that are observed in the dataset, but does not depend on any of the values that are missing.

* MNAR (missing not at random)– the probability that a variable value is missing depends on the missing data values themselves.

### Problems of missing data: 
* Bias and Inaccurate Standard Errors/Hypothesis Tests

### Missing Data Treatment

Five Missing Data Treatments: Listwise Deletion, Pairwise Deletion, Single Imputation, ML Routines, Multiple Imputation

### Practical Guidelines

* Use all available data
* Do not use Single Imputation
	* (Do Not Simply Impute Data Once and Then Proceed as Though You Have Complete Data). Single imputation techniques involve filling in each missing datum with a ‘‘good guess’’ as to what the missing datum should be
* Construct-Level Missingness: Use Maximum Likelihood or Multiple Imputation Missing Data Treatments Whenever 10% or More of The Respondent Sample Is Made Up of Construct-Level Partial Respondents (i.e., Respondents Who Reported on at Least One Construct but Who Omitted at Least One Construct)
* Item-Level Missingness—One Item Is Enough!
	1. When conducting an item-level analysis (e.g., item-level factor analysis or item-level SEM), the analysis should be based on ML or MI missing data techniques.
	2. When conducting a construct-level analysis, if a participant responds to any items (even a single item) from a multi-item scale, then the participant’s average response across the answered items should be used to represent the participant’s scale/construct score.
1. Person-Level Missingness: If the Response Rate Is Below 30%, Report Systematic Nonresponse Parameters and Consider Conducting Sensitivity Analyses