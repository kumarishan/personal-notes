**Table of Contents**

- [Scalaz](#scalaz)
	- [SemiGroup](#semigroup)
	- [Monoids](#monoids)

Scalaz
======
http://eed3si9n.com/learning-scalaz/  

SemiGroup
---------
contains one function append  

Monoids
-------
is a semi-group  
eg:  
Int with 1 and *  
Int with 0 and +  
List[A] with Nil and ++  
A => A with compose and identity  
Boolean with || with false  


in scalaz  
|+| is a monoid +  
monoids compose

```scala
(Monoid[A], Monoid[B]) => Monoid[(A, B)]
(1, "foo") |+| (2, "bar") = (3, "foobar")

Monoid[B] => Monoid[A => B]
f |+| g = (x => f(x) |+| g(x))
mzero[A => B] = (x => mzero[B])