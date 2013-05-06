Bayesian Network
================

_notes made while reading various books on bayesian network_

probability theory
------------------
principle of indifference  
Perspectives - relative frequency and subjective probability  
__fundamentals__  
sample space S - all possible outcomes of experiment  
event - a subset of sample space  

law of total probability  
fundamental rule  
bayes' rule  
conditional independence  
_similarly for variables_  

potential - a real valued function over a domain of finite variables X  
multiplication of potential follows  
- commutative law  
- assicative law  
- domain is union  
- existance of unity  
- distributive law  
projection follows  
- commutative law  
- distributive law  

random variable - a real valued function on sample space  

joint probability distribution  
marginal probability distribution  

general chain rule in probability  

bayesian inference - prior prob, posterior prob, likelihood  

__Markovian Condition__  
given a DAG and a probability distribution over it. Then it satisfies markovian condition if for each variable
it is conditional independent of all the variable's descendents given the set of all its parents

Causal network
--------------
set of variables and directed links - directed graph  

evidence may be transmitted through a serial connection unless the state of the variable in the connection is known  
evidence may be transmitted through a diverging connection unless it is instantiated  
evidence may be transmitted through a convergind connection only if either the variable in the connection or one of
its decendants has received evidence  

d-separation  
markov blanket - parent of A, children of A and variables sharing a child with A  
of markov blanket is instantiated then A is d-separated from the rest of the network  

findig d-separation given an evidence  
- create ancestral graph  
- create moral graph of ancestral graph  
  - connect nodes with common child  
  - drop all direction  
- choose a path avoiding nodes with evidence  

Bayesian Network
----------------
a set of variables and directed edges  
graph is a DAG  
finite mutually exclusive set of state associated with every node  
conditional probability on parents to each ndoe  

if a DAG and a Probability distribution satisfies markovian condition then the distribution
is equal to all the conditional distribution of each node given values of parent  

chain rule of bayesian network - product of all conditional probability tables  
and it satisfies the markovian condition  

evidence in bayesian network  

__conditinal independence__
there can be other conditional independencies than those derieved from markov condition  
entailed conditional independence  
