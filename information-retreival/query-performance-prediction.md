**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [Query Performance Prediction](#query-performance-prediction)
	- [Research Papers](#research-papers)

# Query Performance Prediction

goal of query performance predictor is estimating the effectiveness of the resultant ranking
when no relevance judgements are present  
__uses__
1. improvng retrieval consistency
2. query refinement
3. distributed IR

__categorized into__  
_Pre-retrieval_  
analyze the query expression before search is performed  
linguistic features and/or statistical properties of the query terms distribution
are often used along with some corpus-based statistics  
_Post-retrieval_
analyze also the result list - the result of document most highly ranked.
The Clarity method [6], for example, estimates the
“focus” of the result list with respect to the corpus, as mea-
sured by the KL-divergence between their induced (language)
models.  
Estimating result-list robustness is another effective post-
retrieval prediction paradigm. Intuitively, the more robust
the result list with respect to different factors, the less “dif-
ficult” the query is.  

Effects on he result list of 
- document perturbation
- query perturbation
- query-model identification
- different retrieval functions
are used to device performance metrics


__Notes from Using Document Quality Measures to Predict Web-Search Effectiveness__  
- conclusion using quality measure improve performace  

probability of spam classifier + pagerank score + richness of language used  
post-retrieval query performance predictor (1)  
eg: post-retrieval predictors Cat A and B of ClueWeb  
pre-retrieval predictors (2)  

Clarity Predictor ?? (3)(4)  
coherence and dispersion of result list (5)(6)(7)  

post-retrieval predictors based on analysis of the retrieval scores (8)(9)(10)(11) - severely affected by SEO efforts  

quality measures - spam, stopword, document entropy, inter-document similarity, pagerank
also Combine measure - that integrates the different list-based quality measures by multiplying their values
without normalization and list based quality measure is epsilon-smoothed sum  

IDS - inter document similarity similarity - negative entropy btw non-smoothed language model of di and drichlet smoothed language model of dj  

_Basic predictors_  
clarity predictor Clr and IClr - measures KL divergence between a language model induced from result list and that from corpus (4)(5)(11)  
WIG predictor (8) - higher the difference between the mean retrieval score and the retrieval score of the corpus, the more effective the retrieval  
NQC predictor (9) - standard deviation of retrieval score  
QF predictor (8) - query feedback (11)  
UEF prediction (10)(11)  

document result list for query performance prediction is done using QL - query likelihood model  
log |X|p(q|d) with Dirchlet-smoothed unigram document language models with smoothing parameter = 1000  

QL-SR - list of 1000 doc with spam removed  

Prediction quality is measured using Pearson's correlation (1)  


__Notes from Using statistical decision theory and relevance models for query-performance prediction__  
conclusion - usine reprensentativeness measure of the infomation need gives better performance using UEF

__Notes from Query Performance Predicton in Web Search Environments__
NP-query performance prediction  
techniques produced - WIG, Query Feedback(QF) and Frist Rank Change(FRC)  
_Weighted information gain (WIG)_
use single term and term proximity features to estimate the quality of top retreived results  
good prediction for mixed-query situation with the help of query type classifier  

_Query feedback_
perform better for content based queries  

_FRC_
better for NP-based queries

## Research Papers
1. Estimating the Query Difficulty for Information Retrieval
2. Effective Pre-retrieval Query Performance Pre-diction Using Similarity and Variability Evidence
3. _Predicting Query Performance_
4. Improved query difficulty prediction for the web
5. _What makes a query difficulty ?_
6. Clarity re-visited
7. _On ranking the effectiveness of searches_
8. __Query performance prediction in web search environments__ [####]
9. Predicting Query Performance by Query-Drift Estimation
10. __Using statistical decision theory and relevance models for query-performance prediction__ [#####]
11. Relevance based language models
12. Efficient and effective spam filtering and re-ranking for large web datasets
13. A comparision of user and system query performance predictions
14. Predicting query performance on the web
15. Performance prediction using spatial autocorrelation
16. _Ranking robustness: a novel framework to predict query performance_
17. Inferring query performance using pre-retrieval predictors
18. Query association surrogates for web search
19. Linguistic features to predict query difficulty
20. A survey of pre-retrieval query performance predictors
21. Effective pre-retrieval query performance prediction using similarity and variability evidence
22, The combination and evaluation of query performance prediction methods
23. Ranking robustness: a novel framework to predict query performance
24. _Learning to estimate query difficulty: including applications to missing content detection and distributed information retrieval_
25. __Using Document Quality Measures to Predict Web-Search Effectiveness__ [####]
26. Query hardness estimation using Jensen-Shannon divergence among multiple scoring functions

