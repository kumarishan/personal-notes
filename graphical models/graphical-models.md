**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [Graphical Models](#graphical-models)
	- [Conditional Random Field CRF](#conditional-random-field-crf)
		- [Linar chain CRFs](#linar-chain-crfs)
		- [General CRF](#general-crf)
	- [Factor Graphs](#factor-graphs)
	- [Markov Random Fields](#markov-random-fields)
		- [Combinatorial markov random fields](#combinatorial-markov-random-fields)
	- [Difference between generative and discriminative models](#difference-between-generative-and-discriminative-models)

# Graphical Models

## Conditional Random Field CRF
probabilistic model for structured prediction  
is essentially a way of combining classification with graphical models  
it models conditional dependency unlike joint probability distribution like other generative models  
multinomial logistic regression can be seen as simplest kind of CRF  
discriminative analogue of generative model for structured data  

__Reference__
- An introduction to CRF

### Linar chain CRFs
discriminative analogue of HMM  

### General CRF

## Factor Graphs

## Markov Random Fields

### Combinatorial markov random fields
[source](http://people.cs.umass.edu/~ronb/papers/ecml06.pdf)  

## Difference between generative and discriminative models
generative models are models of joint distribution like naive bayes, hmm. they describe how the output is probabilistically
generated as a function of input.  
discriminative models are models of conditional distribution. It doesnot require probability distribution of input. Something not needed in classification.  
discriminative model is best suited to including rich, overlapping features.  
many family of joint distribution have conditional that take the logestic regression form.  

naive bayes and logistic repgression form the generative-discriminative pair  

generative models can be more natural for handling latent variables, partially-labelled data and unlabelled data. when the data is completely unlabelled then the generative model can be applied in unsupervised fashion. Whereas unsupervised learning in discriminative model is still an active area of research and less natural  

generative models can sometime perform better especially when the dataset is small  
