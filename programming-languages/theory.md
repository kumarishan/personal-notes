**Table of Contents**

- [Programming languages theoritical concepts](#programming-languages-theoritical-concepts)
	- [polymorphism](#polymorphism)
	- [Imperative Programming](#imperative-programming)
	- [Object Oriented Programming](#object-oriented-programming)
	- [Functional Programming](#functional-programming)
	- [expression](#expression)
	- [expression problem](#expression-problem)
	- [side effects](#side-effects)
	- [pure functions](#pure-functions)
	- [referential transparency](#referential-transparency)
	- [Type Class](#type-class)
	- [Monoid](#monoid)
	- [Monad](#monad)
	- [Functor](#functor)
	- [higher order fucntions](#higher-order-fucntions)
	- [Lambda Calculus](#lambda-calculus)
	- [Sequence Point](#sequence-point)
	- [Kinds](#kinds)
	- [References](#references)

# Programming languages theoritical concepts

## polymorphism

## Imperative Programming

## Object Oriented Programming

## Functional Programming

## expression
is a combination of values constants variables
operators and functions that are interpreted according
to the particular rules of precedence and of association which computes
and then return another value  
expression containing functions may have side effect  
expression with side effects doesnot normally have referential transparency  

## expression problem
the expression problem refers to the desire to implement an existing set of abstract
methods for and existing concrete class with needing to change the code that defines either  
normal oop language doesnt allow this  
some languages like Ruby and JS allows it by adding methods to existing concrete object
using wat is called as _monkey patching_  

## side effects
a function is said to have side effect if in addition to returing a result it
also modifies some state or have observable interaction with calling functions  
absence of side effects is necessary but not sufficient condition for referential transparency  
anything that violates referential transparency has side effects  

## pure functions
the function always evaluate to the same result value given the same argument values  
evaluation of the result doesnot cause any observable side effects or output  
if it is referentially transparent for all referentially trasnparent parameters  

## referential transparency
an expression is said to be referential transparent if it can be replaced with its value
without changing the behavior of a program  
helps in improving programs through memoization, comman subexpression elimination and parallelization  
if all are pure function then the expression is referential transparent  

## Type Class
is a type system that supports ad-hoc polymorphism and retroactive polymorphism  
it's different from the classes in oop because there is no such value for this type  
a type class C defines some behaviour in the form of operations that must be supported by a type T
for it to be a member of type class C  
whether the Type T is member or not is not inherent in the type.. simply providing implementations of the
operations that type must support  
always take one or more type parameters  

## Type
universal types
existential types - in java ```List<?>``` and in scala ```List[_]```

## Type Constructor
it builds new type from old  


## Monoid

## Monad
a structure that represents computation  
http://www.intensivesystems.net/tutorials/monads_101.html  
james-iry.blogspot.com/2007/09/monads-are-elephants-part-1.html  
http://scabl.blogspot.in/2013/02/monads-in-scala-1.html  

basically a monad contains to functions bind/flatMap/>>= and result/return/unit/single argument constructor or factory  
it is supposed to amplify types  
for eg:  
Int could be amplified using Maybe monad to accumulate null or execptions  
and when a function takes a value and return and amplified value .. then inorder to compose such functions
we require Monads   

bind/... -> for a monad it takes applies a higher order function to each of the values in a monad (monadic value)  
unit/return/result/... -> takes a term of type A and turns it into a monad fo type M[A], this is
effectively saying it takes a value and return a monadic value  

the functions that are chained are called monadic function  
and the values that are returned are called monadic values  
a monad needs to follow 3 monadic laws  
join/flattern - ????  

Monadic zeros  

all monads are functors  
apply a function that returns a wrapped value to a wrapped value  

monads help in composing funtions that return amplified values (ie monadic values)

examples of monads
- continuation passing syle - continuation monad
- io monad
- maybe
- identity monad
- exception monads - maybe or eitrher
- nullable - possibly missing value of type T
- enumerable - lazily computed list of values of type T
- environment monad or reader monad or function monad - allows a computation to depend on shared environment variable
- state monads - attach state information of any type to a calculation
- writer monads - allows to compute arious kinds of auxillary output which can be "composed" or "accumulated" step by step, in addition to the main result of a computation.
- iteratees
- parsers

monads dont compose, what it means is M[N[A]] is not necessarily a monad if M and N are monad. You cant write a general bind function for M[N[A]] and apply to any level of composition  
[Applicative compose, monad dont](http://stackoverflow.com/questions/7040844/applicatives-compose-monads-dont)  
hence we have monad transformers  


__why exception handling using monad ?__  
because in functional programming we cant have side effect and imperative style exception handling has side effects  
hence use maybe(if two possibilities) or either if many..

### CoMonads

### Monad Transformer
used to add functionality of a monad to another monad
consists of
- type constructor t of kind (* -> *) -> * -> *
- monad operations return and bind
- lift

__read more in detail__  
[Monad transformer](http://eed3si9n.com/learning-scalaz/Monad+transformers.html)  
[Composing Monad](http://ro-che.info/articles/2012-01-02-composing-monads.html)

## Kleisli compostion
is just a compostion that needs extra plumbing to hool together  
for example composing monadic function  

```scala
f: A -> m B
g: B -> m C
(f >=> g ) x = fx >>= g // >= uses bind to express monadic computation

(f >=> g): A -> m C
```

## Functor
is a type class  
for now look into scala treatement  
two functor laws - identity and composition  
apply a function to a wrapped value to get wrapped value

## higher order fucntions
a function that takes a function as parameter and/or returns as function as result  

## Lambda Calculus
http://www.ezresult.com/article/Lambda_calculus  

## Sequence Point
is any poinr in program's execution where it is gauranteed that eer side effects of previous evaluation will have been performed and
no side effects from subsequent evaluation have yet been performed  
eg:  
f() + g() - + is not associated with sequence point hence any of f or g can be evaluated first  
f(), g() - , is a sequence point ensuring f to be evaluated before g  
commonly associated with c and c++ in following places  
* && ||
* ? :
* ;, control statement, loops
* before functions is entered in a function call
* at a function return, after the return value is copied into the calling context
* end of initializer
* between each declarator

## Reification
is the process by which an abstract idea about a computer program is turned into an explicit data model or other object created in a programming language.  
eg:  
- c prog lang reifies the low-level detail of memory addresses
- functional prog reifies procedure abstraction and procedure application in the form of lambda expression
- ClassManifest or TypeTag is used to reifying types. to deal with lost type information in generic types

## Kinds
* [higher-kinded types](http://stackoverflow.com/questions/6246719/what-is-a-higher-kinded-type-in-scala)
* higher kinded type is type constructor that accepts other type constructor like ```class Functor[N[_]]``` - (* -> *) -> * - this particular example converts unary type constructor to a proper type
* 1st order kinded type is a type that accepts other types to create a proper type - * -> * -> * - also a type of binary type cosntructor (via currying) eg: Pair. 
* * -> * is unary type constructor eg: list type constructor
* proper type is a type that u can make a value of also called nullary type constructors - *

## Continuation Passing Style Pattern
is a format of expresssion such that no function ever returns, instead they pass control onto a continuation. conceptually continuation is what happens next.

look at [Swarm](https://code.google.com/p/swarm-dpl/)  
it uses scala delimited continuations plugin to migrate thread between severs as needed. It follows same principle of MapReduce to _move the computation not data_..

### Continuation
is a data structure that represents the computational process at a given point in the process' execution.  
useful for encoding other control mechanism in prog lang like exeption, generators, coroutines, etc  
first-class continuations are constructs that give a prog land the ability to save the execution state at any point and return to that later point in the program.  
are also functional expression for GOTO statement, hence the same caveats apply. good for usage in some special case of web programming, otherwise not suggested.  

continuations allow you to suspend a computation, returning to that computation at any time  
can be used to implement concurrency/cooperative concurrency  
monad can be used to model computation which use CPS  

## CoRoutines

## Generator or semicoroutines

## Communicating Sequential Process

## Polytypic Programming

## References
http://adit.io/posts/2013-04-17-functors,_applicatives,_and_monads_in_pictures.html#just-what-is-a-functor-really  
http://en.wikibooks.org/wiki/Haskell/Understanding_arrows  
