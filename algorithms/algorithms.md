**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [Algorithms](#algorithms)
	- [String Similarity](#string-similarity)
	- [Streaming Algorithms](#streaming-algorithms)
		- [Karp-Papadimitriou-Shenker algorithm](#karp-papadimitriou-shenker-algorithm)
		- [Sticky Sampling](#sticky-sampling)
		- [Lossy counting](#lossy-counting)
		- [Sample and Hold](#sample-and-hold)
		- [Multistage Bloom Filters](#multistage-bloom-filters)
		- [Count-sketch](#count-sketch)
		- [Sketch guided sampling](#sketch-guided-sampling)
		- [Count Min Sketch](#count-min-sketch)
		- [HyperLogLog](#hyperloglog)
		- [K-Minimum Values](#k-minimum-values)
	- [String matching algorithms](#string-matching-algorithms)
	- [Reference](#reference)

# Algorithms

## String Similarity
Edit Distance  
Levenshtein distance - implemented using Wagner Fischer Algo  
[StrikaAMatch](http://www.catalysoft.com/articles/StrikeAMatch.html)
Soundex Algorithm  
Dice's coefficient same as StrikeAMatch  
Hamming distance  
Jaro-Winkler distance  

## Streaming Algorithms
algorithms for processing data streams in which the input is presented as a sequence of items  
this constraints means that an algorithms produces an approximate answer based on a summary or "sketch"

### Karp-Papadimitriou-Shenker algorithm
### Sticky Sampling
### Lossy counting
### Sample and Hold
### Multistage Bloom Filters
### Count-sketch
### Sketch guided sampling
### Count Min Sketch
### HyperLogLog
estimated how many unique items are in a set.
### K-Minimum Values
for counting distinct elements in a data stream

## String matching algorithms
http://www-igm.univ-mlv.fr/~lecroq/string/index.html  
http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.14.7176&rep=rep1&type=pdf  
http://stackoverflow.com/questions/3183582/what-is-the-fastest-substring-search-algorithm  
http://www.chokkan.org/software/simstring/  

Reference
---------
http://www.keithschwarz.com/interesting/  
