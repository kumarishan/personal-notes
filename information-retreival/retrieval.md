**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [Information Retrieval](#information-retrieval)
	- [Different information retrieval models](#different-information-retrieval-models)
		- [Boolean Models](#boolean-models)
			- [Extended Boolean Model](#extended-boolean-model)
		- [Vector Space Models](#vector-space-models)
			- [TfIdf](#tfidf)
			- [Latent Semantic Indexing](#latent-semantic-indexing)
		- [Probabilistic Information retrieval](#probabilistic-information-retrieval)
			- [BM25 and beyond](#bm25-and-beyond)
			- [Neural Network based](#neural-network-based)
			- [Research Papers](#research-papers)
		- [Fuzzy Sets - Set theory based models](#fuzzy-sets---set-theory-based-models)
		- [Inference Networks](#inference-networks)
		- [Discriminative models](#discriminative-models)
		- [Language Models](#language-models)
			- [Effects of smoothing on language models](#effects-of-smoothing-on-language-models)
			- [Structured Language models](#structured-language-models)
			- [Research Papers](#research-papers-1)
		- [Term dependence models](#term-dependence-models)
			- [Markov random field model](#markov-random-field-model)
			- [Research Papers](#research-papers-2)
		- [Graph models](#graph-models)
		- [DFR - Divergence from Randomness](#dfr---divergence-from-randomness)
		- [HMM in IR](#hmm-in-ir)
		- [Statistical Translation](#statistical-translation)
	- [Query and query expansion](#query-and-query-expansion)
	- [Cohesion of result list](#cohesion-of-result-list)
	- [Named Page Finding](#named-page-finding)
	- [Relevance and feedback](#relevance-and-feedback)
	- [Ranking](#ranking)
		- [Research papers](#research-papers)
	- [Cooccurence](#cooccurence)
		- [Research Papers](#research-papers-3)
	- [Information Measures](#information-measures)
		- [Research Papers](#research-papers-4)
	- [Parameter Estimation Methods](#parameter-estimation-methods)
	- [Optimization Techniques](#optimization-techniques)
	- [Statistical Language](#statistical-language)
	- [High Accuracy Retrieval](#high-accuracy-retrieval)
	- [Text Clustering](#text-clustering)
	- [Topic distillation](#topic-distillation)
	- [ReRanking](#reranking)
	- [Concept expansion](#concept-expansion)
	- [Question Answer](#question-answer)
	- [Summarization](#summarization)
	- [Contextual Analysis](#contextual-analysis)
	- [Books](#books)
	- [Other Research Paper](#other-research-paper)

# Information Retrieval

## Different information retrieval models
### Boolean Models
#### Extended Boolean Model




### Vector Space Models
#### TfIdf
#### Latent Semantic Indexing




### Probabilistic Information retrieval
#### BM25 and beyond
#### Neural Network based
#### DFR - Divergence from Randomness
#### Research Papers
1. A neural network for probabilistics information retrieval
2. A Probability distribution model for information retrieval
3. Models for Retrieval with Probabilistic Indexing
4. _The probability ranking principle in IR_
5. A Linguistically Motivated Probabilistic Model of Information Retrieval
6. _Efficient probabilistic inference for text retrieval_
7. Some effective approximation to the 2-poisson model for probabilistic weighting retrieval
8. Information based models for ad hoc IR
9. _Incorporating term dependency in the DFR Framework_



### Fuzzy Sets - Set theory based models




### Inference Networks
1. _Combining the language model and inference network approaches to retrieval_
2. _Indri at Terabyte track 2004_
3. _Evaluation of an inference network-based retrieval model_
4. _Text Retrieval and Inference_




### Discriminative models
1. _Discriminitive models for information retrieval_




### Language Models
is about probability of generating the terms in query from a language model created from documents.
The higher the probability, the more relevant is the corresponding documents to a given query
sparse data problem. Solutions are - a new language model based on a range of data smoothing techniques, including Good 
Turing Estimate, curve-fitting and model combination.  
estimating language models using limited amout of text - smoothing becomes extremely important  

eg:
- Drichlet-smoothed unigram document language models

Language model induction  
Document entropy - high entropy implies richness of language used in the document
calculated using prabability assigned to a term by a language model induced from the document  
eg: document models could be drichlet-smoothed unigram document language models - with u = 0 that is non smoothed
maximum likelihood estimates  

#### Effects of smoothing on language models
LM approach to retrieval - accuracy of smoothing is directly related to accuracy of retrieval  
some smoothing methods perform better for concise title queries and some other for long verbose queries  
possible smoothing are
- Bayesian smoothing using Drichlet prior
- Absolute discounting
- Jelinker Mercer method
other (but less efficient) are Katz, Kneser ney smoothing and Good turing estimate  
in Jelinker Mercer smoothing for web collection, precision depends a lot on smoothing for both large and small queries  
acutally long queries need more smoothing, and less emphasis is placed on the weighting of terms.
in drichlet prior method there is not much difference between long and short queries. but the optimal prior varies from collection
to collection. though remains near 2000.   
in absolute discounting too, precision and recall are much more sensitive to parameter, for long queries than for title queries.  
but the optimal value for parameter doesnot seems to be much different for title and long queries, unlike Jelinker Mercer.  
- In general performance of longer queries is much more sensitive to smoothing parameter value.  
For title queries - Drichlet Prior is better than Absolute discounting and then better than Jelinker Mercer method. It also performerd much better for web collection. also the good performance is relatively insensitive to the choice of smoothing parameter. infact many non optimal run for
drichlet are better than optimal runs of other two.  
for long queries, Jelinker mercer is better than other two. but its avg precision is identical to drichlet.
The three methods all perform better on long queries than title queries.  
avg precision on large database is generally much worse than the smaller ones.. similar to the worst among them  
but precision @10 is better in large databases.  
relative performance of methods remains sam as databse is merged and also the smoothing paramater remain in range  
two roles of smoothing - 
- improve accuracy of the estimated document language model - estimation role
- explain the commong and non-informative words in a query - query modeling
thus drichlet is better for estimation role and Jelinker Mercer is good for query modeling role  
because - drichlet prior adjust prior according to lenght of document. but Jelinker Mercer has fixed smoothing parameter across all documents  
applying backoff strategies worsen the result and make more sensitive to smoothing parameter.  

#### Structured Language models

#### Research Papers
1. __PageRank without hyperlinks: Structural re-ranking using links induced by language models__ [#####]
2. __A general language model for information retrieval__ [###]
3. __A study of smoothing methods for language models applied to ad hoc information retrieval__ [####]
4. __Relevance based language models__ [####]
5. Document Language Models, query models and risk minimization for Information Retrieval
6. __A language modelling approach to information retrieval__ [###]
7. _Language Modelling for information Retreival_
8. _Biterm language models for information retrieval_
9. Clusters, language models, and ad hoc information retrieval
10. _Corpus structure, language models, and ad hoc information retrieval_
11. Utilizing passage-based language models for ad hoc document retrieval
12. _Utilizing passage-based language models for ad hoc document retrieval_
13. _A General Optimization Framework for smoothing language models on Graph structures_
14. _Inter-document similarities, language models, and ad hoc information retrieval_
15. Relating the new language models of information retrieval to the traditional retrieval models




### Term dependence models
#### Markov random field model
will be more effective in large collections, incorporating several types of evidence into a dependence model will further
improve effectiveness  

_basic steps_

* construct a graph representing a query term dependencies to model
* define the set of potentials over the cliques of this graph
* rank documents in descending order

can easily emulate most of the popular retrieval and dependence models such as unigram, bigram and biterm language modelling
the BIM, and the associated methods by which term dependence is modelled  
three variants of MRF - full independence (FI) sequential dependence (SD) full dependence (FD)  
potential function - thought of as a compatibility function - high values to clique settings that are most "compatible" with each other
under the given distribution  
parameter values are trained using - direct maximization approach  

#### Research Papers
1. __A Markov Random Field model for term dependencies__ [#####]
2. _Capturing term dependencies using a language model based on sentence trees_
3. _Term dependence: Truncating the Bahadur Lazarsfeld expansion_
4. _A generalized term dependence model in information retrieval_




### Graph models








### HMM in IR
1. _A Hidden Markov Model Information Retrieval_





### Statistical Translation
1. _Information Retrieval as Statistical Translation_
2. The mathematics of statistical machine translation: Parameter estimation




## Query and query expansion
1. _A language modeling framework for selective query expansion_
2. Query difficulty, robustness and selective application of query expansion
3. _Towards robust query expansion: Model selection in the language model framework to retrieval._
4. Boosting web retrieval through query operations
5. Automatic query expansion using data manifold
6. _Query and Topic Sensitive PageRank for general documents_
7. _Word sense disambiguation in queries_




## Cohesion of result list
measured by its clustering patterns, indicates query performance




## Named Page Finding
1. _Combining document representations for known-item search_




## Relevance and feedback
1. Estimation and use of uncertainty in pseudo-relevance feedback.
2. Navigating in the dark: Modeling uncertainty in ad hoc retrieval using multiple relevance models.
3. A survey on the use of relevance feedback for information retrieval
4. _A two-stage mixture model for pseudo feedback_
5. _Relevance weighting of search terms_




## Ranking
Quality biased ranking- shows features related to stopwords (like stopcover, fracstop), document length, term entropy are most important  
### Research papers
1. __Quality-biased ranking of web documents__ [###]
2. On ranking the effectiveness of searches
3. Document quality models for web ad hoc retrieval
4. _A framework for selective query expansion_
5. A content-based algorithm for blog ranking





## Cooccurence
### Research Papers
1. _A theoritical basis for the use of coccurences data in information retrieval_





## Information Measures
### Research Papers
1. _On generalized information measures and their applications_




## Parameter Estimation Methods
1. _Direct maximization of average precision by hill-climbing with a comparision to a maximum entropy approach_
2. _Direct maximization of rank based metric_





## Optimization Techniques
1. Optimizing search engines using clickthrough data




## Statistical Language
1. Statistical Language Learning
2. Foundations of Statistical Natural Language Processing




## High Accuracy Retrieval
1. _Evaluating high accuracy retrieval techniques_




## Text Clustering
1. _Wikipedia-based smoothing for enhancing text clustering_




## Topic distillation
1. Slash-based relevance propagation model for topic distillation
2. _Topic structure mining for document sets using graph-based analysis_




## ReRanking
1. A study of the integration of passage-, document-, and cluster-based information for re-ranking search results




## Concept expansion
1. _Learning concept importance using a weighted dependence model_
2. _Latent concept expansion using Markov Random Fields_




## Question Answer
1. Bridging lexical chasm: Statistical approaches to answer-finding




## Summarization
1. OCELOT: a system for summarizing web pages




## Contextual Analysis
1. _Improving the effectiveness of infromation retrieval with local context analysis_




## Books
1. _Information Retrieval: Implementing and evaluating search engines_


## Other Research Paper
21. Term weighting approaches in automatic text retrieval
32. _Max-margin Markov networks_
