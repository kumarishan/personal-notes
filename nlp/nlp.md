**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [Natural Language Processing related stuffs](#natural-language-processing-related-stuffs)
	- [Semantic Similarity](#semantic-similarity)
	- [Word-Sense Disambiguation](#word-sense-disambiguation)
	- [Chunking](#chunking)
	- [Sentiment Analysis](#sentiment-analysis)
	- [Part of Speech tagging - POS](#part-of-speech-tagging---pos)
	- [Topic or Context Analysis](#topic-or-context-analysis)
	- [Keyword extraction](#keyword-extraction)
	- [NER - Named Entity Recognition](#ner---named-entity-recognition)
	- [Morphological analysis](#morphological-analysis)
	- [Segmentation](#segmentation)
	- [concordance: key words in context](#concordance-key-words-in-context)
	- [Bigrams](#bigrams)
	- [Bayesian Analysis](#bayesian-analysis)
	- [Automatic Text Summarization](#automatic-text-summarization)
	- [Rapid Automatic Keyword Extraction (RAKE) algorithm](#rapid-automatic-keyword-extraction-rake-algorithm)
	- [Signification phrases](#signification-phrases)
	- [Topic Modelling](#topic-modelling)
	- [Divergence Calculation](#divergence-calculation)
	- [CoReference Resolution](#coreference-resolution)
	- [Reference](#reference)

# Natural Language Processing

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


## Topic or Context Analysis

## Keyword extraction

## NER - Named Entity Recognition


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
- 

## Reference
http://acl.ldc.upenn.edu/P/P01/P01-1005.pdf  
http://www.cs.cmu.edu/~nasmith/LS2/das-martins.07.pdf  
http://research.google.com/pubs/NaturalLanguageProcessing.html  
summarization.com  
http://programminghistorian.org/lessons/topic-modeling-and-mallet  
http://blog.newsle.com/2013/02/01/text-classification-and-feature-hashing-sparse-matrix-vector-multiplication-in-cython/  
