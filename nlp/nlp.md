**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [Natural Language Processing](#natural-language-processing)
	- [Compositionality](#compositionality)
	- [Collocation](#collocation)
	- [Cross language Information Retrieval](#cross-language-information-retrieval)
	- [Anaphora Resolution](#anaphora-resolution)
	- [Discourse analysis](#discourse-analysis)
	- [Discourse modeling](#discourse-modeling)
	- [DataSet transformation](#dataset-transformation)
		- [Preprocessing of data](#preprocessing-of-data)
		- [Feature extraction](#feature-extraction)
			- [Feature Hashing or hashing-trick](#feature-hashing-or-hashing-trick)
			- [Text Feature extraction](#text-feature-extraction)
	- [Tf-Idf term weighting](#tf-idf-term-weighting)
	- [Semantic Similarity](#semantic-similarity)
	- [Word-Sense Disambiguation](#word-sense-disambiguation)
	- [Text Tiling](#text-tiling)
	- [Chunking](#chunking)
	- [Sentiment Analysis](#sentiment-analysis)
	- [Part of Speech tagging - POS](#part-of-speech-tagging---pos)
	- [Stemmer](#stemmer)
		- [porter Stemmer](#porter-stemmer)
		- [Snowball](#snowball)
		- [Krovetz stemmmer](#krovetz-stemmmer)
		- [lancaster stemmer](#lancaster-stemmer)
	- [Topic or Context Analysis](#topic-or-context-analysis)
	- [Keyword extraction](#keyword-extraction)
	- [NER - Named Entity Recognition](#ner---named-entity-recognition)
	- [Morphological analysis](#morphological-analysis)
	- [Segmentation](#segmentation)
		- [Word Segmentation](#word-segmentation)
		- [Sentence Segmentation](#sentence-segmentation)
		- [Text segmentation](#text-segmentation)
	- [concordance: key words in context](#concordance-key-words-in-context)
	- [Bigrams](#bigrams)
	- [Bayesian Analysis](#bayesian-analysis)
	- [Automatic Text Summarization](#automatic-text-summarization)
	- [Rapid Automatic Keyword Extraction (RAKE) algorithm](#rapid-automatic-keyword-extraction-rake-algorithm)
	- [Signification phrases](#signification-phrases)
	- [Topic Modelling](#topic-modelling)
	- [Divergence Calculation](#divergence-calculation)
	- [CoReference Resolution](#coreference-resolution)
	- [Usual steps in NLP](#usual-steps-in-nlp)
	- [Distributional Clustering](#distributional-clustering)
		- [Multiway Distributional Clustering](#multiway-distributional-clustering)
	- [Fog Index](#fog-index)
	- [Text Extraction](#text-extraction)
		- [Table Extraction](#table-extraction)
	- [Maximum Entropy Classifier or Logistic Regression](#maximum-entropy-classifier-or-logistic-regression)
	- [Reference](#reference)

# Natural Language Processing

## Compositionality
a natural language expression is compositional if the meaning of the expression can be predicted from the meanings of the part
idionms least compositional

## Collocation
an expression consisting of two or more words
collocation extracted from technological domains - terminology extraction
limited composibility
uses
- natural language generation
- parsing (preference to natural collocations)
- corpus linguistic research
collocation pos filtering patterns [Technical terminology: some linguistic properties and an algorithm for identification in text]()
 - A N
 - N N
 - AAN
 - ANN
 - NAN
 - NNN
 - NPN - P -> preposition
algos
 - frequency + filtering
 - mean and variance using collocation window (size 9) - if mean is much greater than 1 and a low deviation indicates an interesting phrase
 - mutual information (pointwise mutual information) - mutual information is a good indicator of independence. not a good measure of dependence. reason it depends heavily on each terms occurence. And if a term has very low frequency then it will have heigher rank. Although a cut off frequency of 3 can be used to filter them out. The pointwise mutual information measures the reduction in uncertainity about the occurence of one word when we are told the occurence of the other word.

[The BBI combinatory dictionay of english](http://benjamins.com/#catalog/books/z.bbi)

## Cross language Information Retrieval

## Anaphora Resolution

## Discourse analysis

## Discourse modeling

## DataSet transformation
### Preprocessing of data

### Feature extraction
#### Feature Hashing or hashing-trick
- turning arbitrary features into indices in a vector or matrix
- used for large scale data processing and mining
- using bloom filter instead of feature hashing can increase the error becaause bloom filter uses multiple hash functions
- LSH can be used with feature hashing. for eg: feature hashing reduces the size of features for each item. and LSH can be used to reduce the number of items itself.. because in LSH we find a hash function such that h(a) = h(b) if a and b are similar. 

#### Text Feature extraction
_reference: scikit_
- vectorizer is a general process of turning a collection of text documents into numerical feature vectors
- Bag of words/Bag of n-grams representation
	* this strategy involves tokenizing then 
	* counting the occurrences of tokens in each document
	* then normalizing and weighting
	* weighting with diminishing importance tokens that occur in the majority of samples/documents
	* implemented using sparse vectors
	* limitation - cannot capture pharases and multiword expressions
- tf-idf weighting also tf-idf transformer becasue it transforms the features to numerical presentation
- in a tf-idf vectorization strategy count vectorizer and tfidf weighting is combined
- common vectorizer ie count vectorizer
- n-gram vectorizer
- using hashing to vectorize a large text corpus

## Tf-Idf term weighting
tf: term frequency  
f(t, d): frequency of terms in a document  
tf = f(t,d) _straight away_  
tf(t, d) = 1 _boolean_  
tf(t, d) = log(f(t, d) + 1) _logarithmically_  
tf(t, d) = 0.5 + 0.5 * f(t, d) / maximum raw freq of any term in the document _augmented_  

idf(t, D) = log( |D| / number of documents containing the term + 1 )  

tfidf(t, d, D) = tf(t, d) * idf(t, D)  

 
## Semantic Similarity
__Topological similarity__ - graph based  

_between ontological concepts_  
Edge based  
Node based  

_between ontological instances_  
Pairwise  
Groupwise  

__Statistical Similarity__  
LSA  
Pointwise Mutual Information  

[Semantic Measures](http://www.semantic-measures-library.org/sml/index.php?q=sml-semantic-measures)

## Word-Sense Disambiguation
Supervised Algorithms
- Naive Bayes classification based on words in context window
- Information Theoritic approach - find a single reliable contextual feature that indicates which sense of the ambiguous word is being used. - Flip-Flop algorithm.
- dictionary-based and thesaurus-based

Unsupervised algorithms - sense discrimination
- context-group discrimination/disambiguation

## Text Tiling
breaking document into topically coherent multi-paragraph subparts
cohesion scorer - amt of topic continuity
depth scorer - 
boundary selector

## Chunking

## Sentiment Analysis

## Part of Speech tagging - POS
is an instance of sequence labelling  
rule based - handcrafted rules  
learning based -  
- statistical models - hmm, maximum entropy markov model, conditional random field  
- rule learning - transformation based learning  

useful in  
- word sense disambiguation  
- syntactic parsing  
- information extraction  
  - ner  
  - extract pieces of information relevant to a specific application  
- semantic role labelling/ case role analysis/ thematic analysis/ shallow semantic parsing  
- genomde sequencing  
information retrieval  
- reducing the terms indexed in a  document
  like indexing only nouns, verbs, adjctives, adverbs, interjections, numerals. abbreviations, and participles
  leaving coordinating conjunctions, subordinating conjunctions and determiners, infinite markers, preposition and pronouns  

tag corpus used for training (_see nltk corpus_)
- brown corpus
- treebank corpus
- conil2000

__different pos tagging algorithms__
- NGram Tagger - u b t
- Affix Tagger - learns prefix and suffix patterns of 
- Regex Tagger - regex expressing from [nltk book](http://nltk.org/book/ch05.html) 
- Brill Tagger b
- Classifier based tagger (cpos - classifier based pos tag with naive bayes classifier)
  - significantly slower than raubt (sequential backoff)
  - accuracy of cpos is same as craubt
  - MaxEntTagger - is classifier based tagger - implemented in nltk and stanford nlp
  - other classifier taggers use naive bayes classifier
- HMM based tagger or statistical tagger - [TnT](http://www.coli.uni-saarland.de/~thorsten/tnt/) , hunpos
- memory based tagger - TiMBL
- decision based tagger
- SVM

- using brill tagger always nearly increases accuracy over the inital tagger but not by much

taggers can be chained using Sequential backoff chaining
- one of the highest performer is chain (raubt) - regex, affix, unigram, bigram, trigram
- if a tagger is not able to dertermine tag then its backoff tagger is consulted..
- for example in the above .. first regex will be used if it doesnot find then affix will be used

[perfromance comparision](http://streamhacker.com/2010/04/12/pos-tag-nltk-brill-classifier/)


## Stemmer
### porter Stemmer
### Snowball
### Krovetz stemmmer
### lancaster stemmer
[Official website](http://www.comp.lancs.ac.uk/computing/research/stemming/index.htm)

## Topic or Context Analysis

## Keyword extraction

## NER - Named Entity Recognition
- CRF

## Morphological analysis

## Segmentation
### Word Segmentation
dividing a string of a written language into component words  
it is sometimes used as a prior linguistic processing to tokenization for languages like Chinese where there are no space separation to identify words  

### Sentence Segmentation

### Text segmentation

## concordance: key words in context

## Bigrams

## Bayesian Analysis

## Automatic Text Summarization

## Rapid Automatic Keyword Extraction (RAKE) algorithm

## Signification phrases
Statistically improbable phrase  

## Topic Modelling
topic is a list of words that occur in statistically meaningfull ways  
extracts topic from text  
http://www.cs.princeton.edu/~mimno/topics.html  

## Divergence Calculation
Kullback-Leibler divergence  
Jensen Shannon distance  

## CoReference Resolution


## Usual steps in NLP

- sentence tokenization or sentence segmentation
- word tokenization each sentence
- pos tag/ NER
- stop word removal
- featurization - strings to integer
	* feature hashing
	* dict vectorizer as in sciKit it implements one of K
- tf-idf weighting used as prior to clustering and classification.

- Pos Tags used as complementary tags for training a sequence classifier (eg: a chunker)

## Distributional Clustering
[for text classification](http://blondie.cs.byu.edu/CS652/baker98distributional.pdf)  
[for text categorrization](http://www.cs.huji.ac.il/labs/learning/Papers/sigir.pdf)  
[BiGram HMM with CDC for unsupervised POS](http://www.aclweb.org/anthology-new/W/W10/W10-4109.pdf)  
[Inducing Syntactic categories by context distribution clustering](http://acl.ldc.upenn.edu/W/W00/W00-0717.pdf)  

### Multiway Distributional Clustering
[souce](http://people.cs.umass.edu/~ronb/mdc.html)  
[research paper - detailed implementation](http://people.cs.umass.edu/~ronb/papers/mdc-icml.pdf)  
is an efficient implementation fo Comraf  

## Fog Index
The Gunning readability formula also known as Fog index

## Text Extraction
### Table Extraction
- CRF

## Maximum Entropy Classifier or Logistic Regression

## Reference
http://acl.ldc.upenn.edu/P/P01/P01-1005.pdf  
http://www.cs.cmu.edu/~nasmith/LS2/das-martins.07.pdf  
http://research.google.com/pubs/NaturalLanguageProcessing.html  
summarization.com  
http://programminghistorian.org/lessons/topic-modeling-and-mallet  
http://blog.newsle.com/2013/02/01/text-classification-and-feature-hashing-sparse-matrix-vector-multiplication-in-cython/  
