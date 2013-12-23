**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [Natural Language Processing](#natural-language-processing)
	- [nltk](#nltk)
	- [Mallet](#mallet)
	- [Gensim](#gensim)
	- [OpenNLP](#opennlp)
	- [clojure-opennlp](#clojure-opennlp)
	- [SharpNLP](#sharpnlp)
	- [Pattern](#pattern)
	- [MBSP](#mbsp)
	- [ultraslicklsa](#ultraslicklsa)
	- [Semantic Measure Libraries and Toolkit](#semantic-measure-libraries-and-toolkit)
	- [DISCO - Distributionally related words using Co occurences](#disco---distributionally-related-words-using-co-occurences)
	- [LingPipe](#lingpipe)
	- [Opinion Finder](#opinion-finder)
	- [Tawlk/osae](#tawlkosae)
	- [GATE](#gate)
	- [textir](#textir)
	- [NLP Toolsuite](#nlp-toolsuite)
	- [Stanford NLP Suite](#stanford-nlp-suite)
		- [Stanford NER](#stanford-ner)
		- [Stanford Word Segmenter](#stanford-word-segmenter)
		- [Stanford Classifier](#stanford-classifier)
		- [Stanford POS](#stanford-pos)
		- [Stanfor CoreNLP](#stanfor-corenlp)
		- [Stanford Parser](#stanford-parser)
		- [Phrasal](#phrasal)
		- [Stanford English Tokenizer](#stanford-english-tokenizer)
		- [Stanford TokensRegex](#stanford-tokensregex)
		- [Stanford Temporal Tagger](#stanford-temporal-tagger)
		- [Tregex, Tsurgeon and Semgrex](#tregex-tsurgeon-and-semgrex)
		- [Topic Modeling Toolbox](#topic-modeling-toolbox)
	- [Freeling](#freeling)
	- [TreeTagger](#treetagger)
	- [MEAD](#mead)
	- [Kea](#kea)
	- [Maxent](#maxent)
	- [The Dragon Toolkit](#the-dragon-toolkit)
	- [ScalaNLP](#scalanlp)
	- [Boilerpipe](#boilerpipe)
	- [pignlproc](#pignlproc)
	- [Apache Stanbol](#apache-stanbol)
	- [MaltParser](#maltparser)
		- [pdfssa4met](#pdfssa4met)
	- [GRMM](#grmm)
	- [CRFSuite](#crfsuite)
	- [Factorie](#factorie)
	- [CRF++](#crf++)
	- [Many Others](#many-others)

# Natural Language Processing

## nltk

__python__  


## Mallet
__java__  
statistical natural language processing  

_document classification_
- naive bayes
- maximum entropy
- decision trees
- C45

clustering  

_topic modelling_
* sampling-based implementations of LDA, Pachinko Allocation, and Hierarchical LDA

_information extraction_

_sequence tagging_
* hidden markov models, maximum entropy markov models and crf
* for applications such as NER
numerical optimization - Limited Memory BFGS (an iterative method to solve unconstrained nonlinear optimization problem)  
transforming text document to numerical representation  

## Gensim
__python__  
Topic modelling  
Memory optimized  
Distributed implementation on LDA and LSA/LSI  
Text Transformation - TfIdf, LSI, LDA, Random Projection, Hirarchical LDA(experimental)  
Similarity Calculation  

## OpenNLP
__java__  
* Tokenization  
	* whitespace tokenizer
	* simple - ie sequence of same character class are tokens
	* learnable tokenizer - a maximum entropy tokenizer - detects token boundaries based on probability model
	* tokenization is a two stage process - first sentence detection adn then tokens within each sentence
	* website has english token model to learn from
	* learnable token evaluator
	* tokenizer cross validation using KFold
Sentence Fragmentation  
POS tagger  
Named entity extraction  
chunking  
parsing  
coreference resolution  
document categorization  
machine learning - maximum entropy modelling  

## clojure-opennlp

## SharpNLP
c# port of OpenNLP  

## Pattern
__python__  
data retrieval from Google, Wikipedia, Twitte, Bing, etc  
text analysis - Rule based shallow parser, wordnet interface  
syntactical and semantical n-gram search algorithm  
tf-idf + cosine similarity  
LSA metrics  
clustering & classification  
data visualization  

## MBSP
__python__  
text analysis based on TiMBL & MBT - memory based learning application  
tokenization  
sentence splitting  
POS tagging  
chunking  
lemmatization  
relation finding  
prepositional phrase attachement  
trained on data from WSJ  

## ultraslicklsa
__python__  
LSA module for making search queries  

## Semantic Measure Libraries and Toolkit
__java__  
Graph based similarity measures  

## DISCO - Distributionally related words using Co occurences
__java__  
Semantic similarity using statistical measures  

## LingPipe

## Opinion Finder

## Tawlk/osae

## GATE

## textir

## NLP Toolsuite

## Stanford NLP Suite
### Stanford NER
- conditional random field sequence model
- english and german

### Stanford Word Segmenter
- CRF based word segmenter (arabic, chinese)

### Stanford Classifier
- machine learning 
- for text categorization
- conditional loglinear classifier (aka maximum entropy or multiclass logistic regression model)

### Stanford POS
- maximum entropy (CMM) pos (english, arabic, chinese, french and german)

### Stanfor CoreNLP
- tokenization
- part of speech tagging
- ner
- parsing
- coreference

### Stanford Parser
- probabilistic natural language parser
- highly optimized PCFG and dependecy parser
- lexicalized PCFG parser

### Phrasal
- phrase based machine translation system

### Stanford English Tokenizer
- a fast, efficient and deterministic tokenizer for english text processing
- PTBTokenizer
- work well over Unicode Basic Multilingual Plane that doesnot require word segmentation


### Stanford TokensRegex
- for matching regular expressing over tokens

### Stanford Temporal Tagger
- rule-based temporal tagger

### Tregex, Tsurgeon and Semgrex

### Topic Modeling Toolbox

## Freeling

## TreeTagger

## MEAD
Text summarization open source  

## Kea
Key phrase extraction  

## Maxent
Maximum entropy models  

## The Dragon Toolkit
document representation like - words, multiword phrases
ontology-based concepts and concept pairs  
text retrieval models  
text classification clustering summarization and topic modell;ing  
http://dragon.ischool.drexel.edu/features.asp  

## ScalaNLP

## Boilerpipe

## pignlproc
apache pig utilities to build training corpora for machine learning/NLP out of public Wikipedia and DBPedia dumps  

## Apache Stanbol
set of reusable components for semantic content management  

## MaltParser
system for data driven dependency parsing  

### pdfssa4met
PDF structure and syntactic analysis for Metadata Extraction and Tagging

## GRMM
## CRFSuite
## Factorie
## CRF++

## Many Others
http://opennlp.sourceforge.net/projects.html  
http://boston.lti.cs.cmu.edu/clueweb09/wiki/tiki-index.php?page=ClueWeb09%20Wiki  
