**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [Data Structures](#data-structures)
	- [B-K Tree](#b-k-tree)
	- [Trie](#trie)
		- [LOUDS-based trie](#louds-based-trie)
		- [Compacted double-array trie](#compacted-double-array-trie)
		- [MARISA trie](#marisa-trie)

# Data Structures

## B-K Tree
data structure for spell checking based on levenshtein distance  
can use another string similarity function like [StrikeAMatch](http://www.catalysoft.com/articles/StrikeAMatch.html)  

## Trie
### LOUDS-based trie
### Compacted double-array trie
### MARISA trie
Matching Algorithm with Recursively Implemented StorAge (MARISA)  
static memory efficient trie data structure  

A marisa based dictionary supports not only lookupt but also reverse lookup, common prefix search and predictive search
- lookup to check whether or not a given string exists in a dictionary
- reverse lookup is to restore a key from its ID
- common prefix search is to find keys from prefixes of a given string
- predictive search is to find keys starting with a given string

much more efficient than Compacted double array trie and LOUDS-based trie  
[libmarisa](https://code.google.com/p/marisa-trie/)
