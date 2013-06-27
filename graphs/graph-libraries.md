**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [Graph Libraries](#graph-libraries)
	- [SNAP - Stanford Network Analysis Platform](#snap---stanford-network-analysis-platform)
	- [Cassovary - Twitter](#cassovary---twitter)
	- [GraphLab - BigLearning on Graph - CMU](#graphlab---biglearning-on-graph---cmu)
		- [GraphChi](#graphchi)
	- [JUNG](#jung)
	- [fastgraph](#fastgraph)
	- [What i need ?](#what-i-need-)
	- [Reference](#reference)

Graph Libraries
===============

SNAP - Stanford Network Analysis Platform
-----------------------------------------
__C/C++__

Cassovary - Twitter
-------------------
__Scala__  
uses java scala collection as data structures

GraphLab - BigLearning on Graph - CMU
-------------------------------------
__C++__  
multicore and distributed  
collaborative filtering  
graphical modelling  
graph analytics  
clustering  
topic modelling  
asynchronous  
asynchronous distributed graph computation  

### GraphChi
__C++__  
disk based large scale graph computation  

JUNG
----
__java__
directed/undirected graphs  
multi-model graphs  
parallel edges  
hypergraphs  
clustering  
decompostion  
optimization  
random graph generation  
statistical analysis  
network distance  
flows  
importance measure  
visualization framework  

fastgraph
---------
__java__  
uses Javolution  
implemented mainly for benchmark purpose  

What i need ?
-------------
A Graph Library in Scala  
Ability to run graph algos on Spark Cluster  
Using High Performance Collections like HPPC or Trove  
JUNG could be a good option only problem it uses Common Collections so may not be highly optimized  

This graph library to be used for Graphical Models as in GraphLab  

Reference
---------
http://strata.oreilly.com/2012/12/graphchi-graph-analytics-over-billions-of-edges-using-your-laptop.html  
