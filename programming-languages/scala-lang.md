**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [Scala Language](#scala-language)
	- [Imports](#imports)
	- [Option](#option)
	- [Array](#array)
	- [Control Structures](#control-structures)
	- [Functions/Methods](#functionsmethods)
	- [Class](#class)
	- [Case Class](#case-class)
	- [Extractor Objects](#extractor-objects)
	- [Types](#types)
		- [Compound types](#compound-types)
		- [Type ascription](#type-ascription)
		- [Variance](#variance)
			- [Covariant subtyping](#covariant-subtyping)
			- [Contravariant subtyping](#contravariant-subtyping)
			- [Variance positions](#variance-positions)
		- [Existential types](#existential-types)
	- [View Bounds](#view-bounds)
	- [Context Bounds](#context-bounds)
	- [Type-lambda](#type-lambda)
	- [Exception](#exception)
	- [Annotations](#annotations)
	- [File](#file)
	- [Arrays](#arrays)
	- [List](#list)
	- [Tuples](#tuples)
	- [Sets](#sets)
	- [Map](#map)
	- [Functional Programming](#functional-programming)
		- [Monad in Scala](#monad-in-scala)
		- [Functor](#functor)
		- [Applicative](#applicative)
	- [Array](#array-1)
	- [Control Structures](#control-structures-1)
	- [Continuations](#continuations)
	- [ClassManifest and TypeTag](#classmanifest-and-typetag)
	- [Quirks](#quirks)

# Scala Language

http://docs.scala-lang.org/tutorials/FAQ/finding-symbols.html  
http://docs.scala-lang.org/cheatsheets/  
http://apocalisp.wordpress.com/  
http://danielwestheide.com/scala/neophytes.html  

## Imports
- import p._  all members of p (this is analogous to import p.* in Java).
- import p.x  the member x of p.
- import p.{x => a}   the member x of p renamed as a.
- import p.{x, y} the members x and y of p.
- import p1.p2.z  the member z of p2, itself member of p1.

## Option

using option as returning result and passing parameters enables us to avoid ifs for null checks  
use getOrElse instead of if(...)  
use for comprehension to perform a series of operation only if something was passed as parameters  
Option is a monad and can be visualized as a List of two

## Array

its a function  

```scala
class Array[T](l: int) extends (Int => T) {
    def apply(i: Int) = ...
}
```

## Control Structures

implementing new control structures

```scala
//mandates that T has close function
def using[T <: {def close()}](resource: T)(block: T => unit)(
    try {
        block(resource)
    } finally {
        if(resource != null) resource.close()
    }
)

using(new BufferedReader(new FileReader(path))){
    f => f.readLine()
}
```

## Functions/Methods

by default parameters are val  
procedure - a method executed only for its side effect - defined without = and return type  

```scala
val f = (_: Int) + (_: Int) // have to mention type for each placeholder
a.foreach(println _) // a.foreach(println(_)) partially applied function

def sum(a: Int, b: Int) = ...
val a = sum _
val b = sum(1, _: Int)
b(3) // b.apply(1, 3) = b(1, 3)

def m(x: Int){} // implicit return type Unit
```
[implicit parameters](http://docs.scala-lang.org/tutorials/tour/implicit-parameters.html)

```scala
abstract class SemiGroup[A] {
    def add(x: A, y: A): A
}

abstract class Monoid[A] extends SemiGroup[A]{
    def unit: A
}

object Test extends App {
    implicit object IntMonoid extends Monoid[Int]{
        def add(x: Int, y: Int): Int = x + y
        def unit: Int = 0
    }

    implicit object StringMonoid extends Monoid[String]{
        def add(x: String, y: String): String = x concat y
        def unit: String = ""
    }

    def sum[A](x: List[A])(implicit m: Monoid[A]): A = ...

}
```
[automatic type-dependent closure](http://docs.scala-lang.org/tutorials/tour/automatic-closures.html)  
parameterless function names are parameters for method  

```scala
def whileLoop(cond: => Boolean)(body: => Unit){
    if(cond){
        body
        whileLoop(cond)(body)
    }
}

var i = 10
whileLoop(i > 0){
    
}

//another example
def loop(body: => Unit): LoopUnlessCond = new LoopUnlessCond(body)

class LoopUnlessCond(body: => Unit){
    def unless(cond: => Boolean){
        body
        if(!cond) unless(cond)
    }
}

loop {
    ..
} unless( i > 0)
```


## Class

[inner class](http://docs.scala-lang.org/tutorials/tour/inner-classes.html)
__Implicit Class__
[implicit classes](http://docs.scala-lang.org/overviews/core/implicit-classes.html)
* implicit class makes it primary constructor available for implicit conversion
* they can only be defined inside trait/class/object
* they can have only one non-implicit member

```scala
implicit C(x: Int)(implicit i: Int) ...
```
* there may not be any method, member of object or object in the scope with the same name as that of implicit class
* an object with same name as class is companion object and has to be in same source file
* a class and its companion object can access the private members
* use require for precondition check in constructor
* another objects class parameters cannot be accessed - it will need to be converted to field
* auxillary constructor - def this() = this(0) .. - must invoke another constructor of same class as first action

## Case Class
it makes sense to use case class if pattern matching is used to decompose structure  

## Extractor Objects

```scala
object T {
    def apply(x: Int): Int = ...
    def unapply(x: Int): Option[Int] = ...
}
val x = T(23)
x match { case T(n) => ... }
```
return type of unapply  
- if its a test return Boolean, like case even()
- if its a value return Option[T]
- if its a list Option[(T1, T2,...)]

## Types

### Compound types
written using with eg: ```A with B with C { refinement }```

### Type ascription
tells the compiler what type u expect out of an expression of all the valid types better than using asInstanceOf

### Variance

#### Covariant subtyping
a bit of background  
if we define a class as  

```scala
class A[T]
class B
class C extends B
```
here C is subtype of B but is A[C] subtype of A[B] ?? well if u try this 

```scala
val a: A[B] = new A[C]
Note: c <: B, but class A is invariant in type T.
You may wish to define T as +T instead. (SLS 4.5)
       val a:A[B] = new A[c]
                    ^
```
it gives error because class A is invariant in type T  
what we want is that class A to be covariant in type T ie.  
if type S is subtype of T then A[S] is also subtype of A[T] - this is called covariant(flexible) subtyping  
and defined as  

```scala
class A[+T]
```
orders types from more specific to mroe generic

using lower bound to solve the problem of using covariant type in method parameters

```scala
class A[+T]{
    def m[B >: A](b: B): A = ...
}
```
it will now accept A or any super type of A

#### Contravariant subtyping
its opposite of covariant ie  

```scala
class A[-T]
class B
class C extends B
```
then A[B] is a subtype of A[C] ie

```scala
val a: A[C] = new A[B]
val a: A[B] = new A[C] //error
```
orders types from more generic to more specific

#### Variance positions
* \- annotated type parameter can be used in only negative position inside the class similarly \+ annotated only in positive positions
invariant type can be used in any position negative/positive/neutral
* positions at the top level of class is classified as positive
* method value parameter positions and type parameters of the method are classified as flipped
* classification is flipped at type argument position of a type if it is annoted with \-. if it has no variance annotation then it is changed to neutral
* function's arguments are contravariant positions, but return type is covariant evident from the fact that function's are defined as

```scala
class Function1[-T1, +R]
class Function2[-T1, -T2, +R] // and so on
```
eg:

```scala
class A[-T, +U]{
    def m[W-](a: T-, b: A[U+, T-]-): A[A[U+, T-]-, U+]+ = ...
}
```
* variance is not applicable to mutable state

```scala
class A[+T]{
    var a: T // generates a setter def t_=(t: T){ this.t = t}
}
```
even though T is covariant its usage in t_'s parameter is legal

### Existential types
mostly used while accessing java class with wildcards eg: ```Iterator<?>```  

```scala
Iterator<?> in scala is Iterator[T] forSome {type T}
Iterator<?> extends Component> in scala is Iterator[T] forSome {type T <: Component}

Iterator[_] is shortform for Iterator[T] forSome {type T}
```
in scala if u use _ as a placeholder for types then it makes an existential type  


## View Bounds

enable to use type A as if its type B  

```scala
def f[A <% B](a: A) = a.bMethod
def f[A](a: A)(implicit ev: A => B) = a.bMenthod //de-sugared
````
wat it means is the that there should be some implicit conversion from A to B such that one can call B methods  
on object type of A.
eg:

```scala
def f[A <: Ordered[A]](a: A, b: A) = if (a < b) a else b
// because A can be converted to Ordered[A] and then Ordered has method <(other: A): Boolean hence we can use a < b
```

used for _pimp my library_ pattern which allows adding new methods to existing type, in situation u want to return the original type  

## Context Bounds

Type class pattern:  
requires a parametrized types  
it describes an implicit value  
it is used to declare that for some type A there is an implicit value of type B[A] available  

```scala
def f[A : B](a: A) = g(a) // where g requires a implicit value of type B[A]
def f[A](a: A)(implicit ev: B[A]) = g(a) //de-sugared

def sum[A: Monoid](xs: List[A]): A = {
    val m = implicitly[Monoid[A]
    xs.foldLeft(m.mzero)(m.mappend)
}

def f[A : Ordering](a: A, b: A) = implicitly(Ordering[A]).compare(a: A, b: A)

```

## Type-lambda

* higher
* is like currying the type system
* [higher-kinded types](http://stackoverflow.com/questions/6246719/what-is-a-higher-kinded-type-in-scala)
* higher kinded type is type constructor that accepts other type constructor like ```class Functor[N[_]]```
* 1st order kinded type is a type that accepts other types to create a proper type
* proper type is a type that u can make a value of

## Exception

in order for java to be able to catch exception

```scala
@throws(classOf[IOException])
def read() = ...
```

## Annotations

if using java annotations make sure to use -target:jvm-1.5 option  

```java
@interface AnnotEx {
    public String value();
    public String mail() defailt "";
}
```

```scala
@AnnotEx("a value", mail = "email")
class MyClass ...
```

## File

* scala.io.Source
* Source.fromFile(filename).getLines().toList

## Arrays

* always immutable

## List

* List() or Nil
* :::, ::, (n)
* drop(), dropRight()
* reverse, count, mkString
* exists, filter, forall, foreach, map, remove, sort
* head, init, last, tail
* isEmpty, length
* reduceLeft
* always immutable

## Tuples

* _1, _2
* contain different types

## Sets

* both mutable and immutable
* default is immutable set
* to create mutable using Set() import mutable.Set
* +=, +

## Map

* both immutable and mutable
* +=, ->

## Functional Programming

### Monad in Scala

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


### Functor

its a class with map  
it aply a function to a wrapped data to get a wrapped data

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

### Applicative

apply a wrapped function over wrapped data to get a wrapped data

## Array

its a function  

```scala
class Array[T](l: int) extends (Int => T) {
    def apply(i: Int) = ...
}
```

## Control Structures

implementing new control structures

```scala
//mandates that T has close function
def using[T <: {def close()}](resource: T)(block: T => unit)(
    try {
        block(resource)
    } finally {
        if(resource != null) resource.close()
    }
)

using(new BufferedReader(new FileReader(path))){
    f => f.readLine()
}
```
## Continuations
[Example code](https://github.com/kghost/scala-continuation-sample/blob/master/src/main/scala/test/Main.scala)
[Continuation monad](http://blog.tmorris.net/posts/continuation-monad-in-scala/)

## ClassManifest and TypeTag

## Quirks

* ```=>``` is a class hence can be subclassed eg: Arrray  
* breaks in scala can be used like

```scala
import scala.util.control.Breakable._
breakable {
    for(x <- 1 until 5){
        if (x > 3) break
    }
}

// implementation
def breakable(op: => Unit){
    try {
        op
    } catch{
        case ex: BreakException => 
    }
}

def break = throw breakException
```
* anonymous function without parameters - see Breakable implementation and usage and automated type-dependent closure
* remember semicolon required here

```scala
def a(x: Int) = x.negate;
```

* in scala it is possible to tie a class to another type (which will be implemented in future) by giving self reference
this the other type explicitly

```scala
class NodeImpl extends NodeI {
    self: Node =>
    ...
}
```

* (1.0 / 0) isInfinity, 4 to 6 = Range(4, 5, 6), "bob" capitalize, "robert" drop 2 = "bert", 0 max 5
* to get the implicit value of a type implicitly[Type]
* to pass a sequence to a varargs function use type ascription to _*  ```Set(values: _*)```
* design patterns on actors and more [Let it Crash](http://letitcrash.com)