Organization of unlabeled data into similar groups.

**Cluster:** A collection of data where the items in the collection are similar to one another and dissimilar to other collections.

### Distance Between Clusters

* Single Link
	* The distance between two clusters is the distance between the two closest points in each cluster
* Complete Link
	* Distance between furthest data points.
* Average
	* Distance between two clusters is average distance of all pair-wise distances
* Centroid
	* Center of each cluster.
* Ward
	* Calculate the sum of squares. The two clusters with the smallest increase in the overall sum of squares within cluster distances are combined.
	
* Average and Ward's are the most performant.
## Dendrograms 

* Can be used to identify the number of clusters in the data
* Well-formed clusters
* Outliers

## Cluster Visualization

* Scale data before doing clustering.
* Save the scaling rationale and do it on any data points in the future to cluster them.
* The height of the joint = distance between two merge clusters
* The merge distance monotonically increases as we merge more and more for single, complete and average linkage methods, not for the centroid method
* Can provide some understanding about how many natural groups there are in the data.
* Drastic height changes = very different clusters!
* 


# K-Means Clustering

* Assume number of clusters k is given.
* Randomly choose k examples as seeds, one for each cluster
* Form initial clusters based on the seeds
* iterate by repeatedly re-allocating instances to different clusters to improve the clustering
* Stop when clustering converges or after a fixed number of iterations

### Weaknesses

* Very sensitive to outliers
* Outliers leads to very unreasonable clusters that make no sense
* Remove outliers before running k-means
	* k-medoids is an alternative method and is more robust to outliers

## Evaluating Clusters: Internals

* By user interpretation
* Not really a good way to evaluate in general
* Internal criterion: good clustering produce high quality cluster
## Evaluating Clusters: Externals

* If true class labels arek nown, the validity of a clustering can be verified
* Given partition P and ground truth G, measure the number of vector pairs with various attributes