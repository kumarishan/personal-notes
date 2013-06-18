Scala Language
==============
http://docs.scala-lang.org/tutorials/FAQ/finding-symbols.html  
http://docs.scala-lang.org/cheatsheets/  

Option
------
using option as returning result and passing parameters enables us to avoid ifs for null checks  
use getOrElse instead of if(...)  
use for comprehension to perform a series of operation only if something was passed as parameters  
Option is a monad and can be visualized as a List of two 

Monad in Scala
--------------
all containers and Options is a monad  
scala does not mandate declaration of flatten but mandate flatMap and map, to enable its usage with for comprehenssion  

flatMap == flatten(map()) - can be implemented via flatten and map  

```scala
def flatMap[B](f: A => M[B]): M[B] = ..  
```

flatten: M[M[A]] -> M[A]  
eg:  

```scala
def flatten[A](outer: Option[Option[A]]) : Option[A] =
  outer match {
    case None => None
    case Some(inner) => inner
  }
```

map: can also be implemented via flatMap and constructor/unit  

```scala
def map[B](f: A => B):M[B] = flatMap {x => unit(f(x))}
def unit[A](x:A): M[A] = ..
```

a monad can be class, case class or trait  
bind is eqv to flatMap  
join is eqv to flatten  
and result/unit is eqv to new M(v) or just M(v)  

chaining using monad (to avoid null checks) as done using do/domonad in pure functional lang is done in scala using for comprehension  
for {
    a <- ....
    b <- ....
} yield ...

__Laws__  
Identity: First Monad law

```scala
m flatMap unit eqv m
m flatMap { x => unit(x)} eqv m
m flatMap { x => unit(identity(x))} eqv m
m map { x => identiy(x)} eqv m

for (x <- m; y <- unit(x)) yield y eqv m
```
Unit: Second monad law

```scala
unit(x) flatMap f eqv f(x)
unit(x) flatMap {y => f(y)} eqv f(x)

for (y <- unit(x); result <- f(y)) yield result eqv f(x)

unit(x) map f eqv unit(f(x))
unit(x) map f eqv unit(x) flatMap { y => unit(f(y))}

for ( y <- unit(x) ) yield f(y) eqv unit(f(x))
```

Composition: Third monad law

```scala
m flatMap g flatMap f eqv m flatMap {x => g(x) flatMap f}
m flatMap {x => g(x)} flatMap {y => g(y)} eqv m flatMap {x => g(x) flatMap { y => f(y)}}

for (a <- m; b <- g(a); result <- f(b)) yield result eqv
for (a <- m; result <- for (b <- g(a); t <- f(b)) yield t) yield result
```

for
---
for comprehension is a way to execute monads (eqv to do in clojure like purely functional prog lang)  

if for is used with yield then its converted using recursive flatMap and map  
eg:  

```scala
for (n <- a; m <- b) yield n op m
```
is eqv to  

```scala
a flatMap {n => b map { m => n op m }}
```
eqv to  

```scala
a flatMap {n => b flatMap { m => unit(n op m) }}
```

if its devoid of yield then its implemented using foreach, this is called imperative form of for  
for (n <- a; m <= b) println n op m  
a foreach {n => b foreach { m => println n op m}}  

foreach is needed if you want to use the imperative form of for  

__for with gaurds__ if  

```scala
for ( n <- a if nexpr) yield n  
a filter { n => expr } map n => n  
```

__Monadic zeros__
Identity: first law of zero

```scala
mzero flatMap f  eqv mzero
mzero map f eqv mzero
```
M to Zero in Nothing Flat: Second law of zero

```scala
m flatMap { x => mzero } eqv mzero
```

Plus: Third and fourth zero law
for monads with zero they have plus for eg.. List with ::: and Option with orElse  

```scala
class M[A] {
    def plus(other: M[B >: A]): M[B] = ...
}

mzero plus m eqv m
m plus mzero eqz m
```

flterrable monad implements filter  

```scala
class M[A] {
    def map[B](f: A => B): M[B] = ...
    def flatMap[B](f: A => M[B]):M[B] = ...
    def filter(f: A => Boolean): M[A] = ...
}

m filter p eqv m flatMap {x => if(p(x)) unit(x) else mzero }
m filter { x => true} eqv m
m filter {x => false} eqv mzero
```


Functor
-------
its a class with map  

```scala
class M[A] {  
  def map[B](f: A => B): M[B] = ..  
}  
```

identity law  
for functor m  

```scala
m map identityFunc eqv m  
m map { x => identity(x)} eqv m  
m map { x => x} eqv m  
```
composition law  

```scala
m map g map f eqv m map { x => f(g(x))}  
eg:  
m map g map f == m map (f compose g)  
for ( x <- (for (y <- m) yield g(y))) yield f(x) eqv for (x <- m) yield f(g(x))  
```

functor/monad connection law  

```scala
m map f eqv m flatMap {x => unit(f(x))}
for(x <- m) yield f(x) eqv for(x <- m; y <- unit(f(x))) yield y

flatten(m map identity) eqv m flatMap identity
flatten(m) eqv m flatMap identity
```
