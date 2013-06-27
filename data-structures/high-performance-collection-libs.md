**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [List of high performance collection libraries](#list-of-high-performance-collection-libraries)
	- [HPPC - High Performance Primitive Collection](#hppc---high-performance-primitive-collection)
	- [Trove](#trove)
	- [Colt](#colt)
	- [Mahout - Math](#mahout---math)
	- [PCJ - Primitive collection for java](#pcj---primitive-collection-for-java)
	- [Javolution](#javolution)
	- [fastutil](#fastutil)
	- [note](#note)

List of high performance collection libraries
==============================================

HPPC - High Performance Primitive Collection
--------------------------------------------
__java__  
best in performance overall  
good documentations  
very fast direct access to underlying storage, which makes it faster  
all primitive types and Object type supported  
lists, Set and maps  
only problem is that its in alpha stage as of this writing  

Trove
-----
__java__  
no proper documentation  
benchmarks generally favours in most conditions  
both primitive and object type supported  
all combination of primitive and object as key-value supported for maps  
Open addressing scheme followed  
Easily extendible  

Colt
----
_java__  
__cern__'s library  
contains high perfomance implementation of various collections  
BitVectors, matrix, maps and lists  
maps generally have Object as datatype  
separate classes for key's type  
contains various other libraries for computing  

Mahout - Math
-------------
__java__  
collection used in mahout algorithms  
accessible as separate package mahout-math  
mostly influenced by colt  

PCJ - Primitive collection for java
-----------------------------------
__java__  
_find more_

Javolution
----------
__java__  
_find more_

fastutil
--------
__java__  
_find more_

note
----
overall it looks like HPPC is a good option to use when developing frameworks or libraries
But others can equally find their uses in specific applications