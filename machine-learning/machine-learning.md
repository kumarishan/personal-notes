**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [Machine Learning Algorithms](#machine-learning-algorithms)
	- [Supervised Algorithms](#supervised-algorithms)
	- [Unsupervised Algorithms](#unsupervised-algorithms)
		- [KMeans](#kmeans)
			- [MiniBatchKMeans](#minibatchkmeans)
			- [Streaming KMeans](#streaming-kmeans)
		- [X-Means](#x-means)
	- [Topological data analysis](#topological-data-analysis)
	- [Deep Belief Networks](#deep-belief-networks)
	- [Deep Machine Learning](#deep-machine-learning)
	- [Deep Boltzmann Machine](#deep-boltzmann-machine)
	- [Instance based learning](#instance-based-learning)

# Machine Learning Algorithms

## Supervised Algorithms


## Unsupervised Algorithms
### KMeans
a generic implementation of kmeans usually have these parameters as input
- dataset to cluster
- number of clusters
- maximum number of iterations
- empty cluster policy - ie whether to allow an empty cluster or discard them
- distance metric - ie how to calculate distance
- overclustering factor - ie inorder to get n clusters actually find n*f clusters and then merge where f is overlclustering factor.
- initial partition policy - how to select initial set of clusters - kmeans++, random, or custom. This is usually provided with the number of clusters and then it internally chooses seed points hence
- whether to pre-compute distances ?

results
- centroids of clusters
- clusters assignments ie.. dataset grouped in clusters
- or both

#### MiniBatchKMeans
online implementation that does incremental updates of the centers position. much faster to standard batch implementation for large scale (data sample > 10K)

#### Streaming KMeans
https://issues.apache.org/jira/browse/MAHOUT-1154

### X-Means

## Topological data analysis

## Deep Belief Networks

## Deep Machine Learning

## Deep Boltzmann Machine

## Instance based learning

