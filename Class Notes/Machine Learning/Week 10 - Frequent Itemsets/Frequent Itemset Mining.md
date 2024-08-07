Market-Basket Model

* Defines many-many relationship between items and baskets
* The frequent itemsets problem is that of finding sets of items that appear in (are related to) many of the same baskets

Market-Basket Analysis

* We have items and baskets, sometimes called transactions.
* Each basket consists of a set of items (an itemset)  and usualyl we assume that the number of items in a basket is small, much smaller than the total number of items.
* The number of baskets is usually assumed to be very large.

Definitions
* A set of literals called items (think items in basket)
* Transaction T: a set of items such that T <_ i
* Dataset D: a set of Transactions
* A transaction T contains X a set of items in I if X <_ I
* The rule X -> Y has support s in transaction set D if s% of transactions in D contain X u Y
* The rule X -> holds in transaction set D with confidence c if C% of transaction D that contain X also contain Y


![[lesson10_marketbaskettable.png]]

In the Market Basket Analysis:
* Itemset: a collecction of one or more items (milk, bread, diaper)
	* k-itemset, an itemset containing k items
* Support count 
	* Frequency of an itemset
		* o(milk bread diaper) = 2
* Support(s)
	* Fraction of transactions containing an itemset
		* FREQUENCY OBSERVED
	* s(Milk, Bread, Diaper) = 2/5
* Frequent Itemset c
	* One whose support is greater than or equal to a **minsup** threshold
![[lesson10_mba_associationexample.png]]

### Applications of Frequent Itemsets

* Market basket analysis
* Related concepts
	* Let items be Words, and baskets be documents (web pages, etc.)
	* Ignoring the most common words, then we could hope to find among the frequent pairs some pairs of words that represent a joint concept
* Biomarkers
	* Let the items be of two types -- biomarkers such as genes, blood proteins, and diseases. Each basket is the set of data about a patient, their genome, blood-chemistry analysis, as well as their medical history of disease
	* A frequent itemset that consists of one disease and one or more biomarkers suggests a test for the disease

Why use Support and Confidence?

* Low support means it could be just a rule by chance
* A low support rule is not interesting from a business perspective
* Confidence measures the reliability of the inference made by a rule

Association Rules should be interpreted with **caution**.
* They do not imply causality which requires extra knowledge of the data
* Instead they simply imply a strong co-occurrence relationship between items

Confidence alone can be useful. **Interest** is when there's a calculation of confidence and fraction.


### The Association Rule Mining Problem

Brute-force Approach
	* List all possible association rules
	* Compute the confidence and support for each rule
	* Prune rules that fail the minsup and minconf thresholds

Two-Step Approach
* Frequent Itemset Generation
	* Generate all itemsets who support >= minsup
* Rule Generation
	* Generate high confidence rules from each frequent itemset

## Frequent Itemset Generation

For a set with n-items we have 2^n - 1 possible itemsets

Each of these is called a candidate frequent itemset

Compare each candidate against every transaction
* O(NMw) time complexity

Several ways to reduce the computational complexity
* Reduce the number of candidate itemsets (M) by pruning the itemset lattice
	* Apriori Algorithm
* Reduce the number of comparisons by using advanced data structures to store the lattice

## Apriori Algorithm

* Intuition
	 * Apriori algorithm reduces the number of candidate itemsets (M) by pruning the dataset
* Details
	* If we identify an itemset as being infrequent, its subsets should not be generated/tested
	* Algorithm:
		* Iteratively generate candidates with length (k+1) from the frequent itemsets with length k
		* Test candidates against dataset of transactions
		* Update k and repeat the process
* All subsets of a frequent subset must also be frequent
* Methods like the Fk-1 x Fk method
* Other methods Fk-1 x Fk-1 method
	* Merge pairs of frequent (k-1) itemsets only if their first k - 2 items are identical

Generating Association Rules

* For each frequent itemset f, generate all nonempty subsets of f
* For every non-empty subsets s of f output the rule s -> (f ~ s)
	* if support count(f) / support (count s) >= minconf
	* 
Apriori is **expensive**

Can leverage a tree-like structure or graph structure to create an FP-Tree. This tree structure will maintain the association between the itemsets.

## FP Tree

Step 1: The dataset is scanned once to determine the support count of each item. Infrequent items are discarded, while the frequent items are sorted in increasing order.
Step 2: A second pass over the dataset is used to construct an FP-Tree. After reading the first transaction a, b, the nodes a and b are created. A path is then formed from null -> A -> B to encode the transaction. Every node along the path has a frequency count of 1.
Step 3: After reading the second transaction b, c, d, a new set of nodes is created for items b, c, and d. A path is formed to represent the transaction by connecting nodes null --> B --> C --> D
...
etc.

![[lesson10_fptree.png]]![[lesson10_fpgrowthitemsets.png]]

There are also Conditional FP-Trees...etc.

**Apriori Vs. FP-Growth**

Do not use Apriori, FP-Growth beats apriori with less memory usage and runtime. FP-growth is more scalable because of its linear running time. 

## Maximal and Closed Frequent Itemsets

What happens when you have lots of items in your basket?

Itemsets can grow exponentially and creates problems for storage.

Maximal and closed frequent itemsets help us create smaller subsets.

Lift of Assocation Rules...