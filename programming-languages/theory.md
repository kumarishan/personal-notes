Programming languages theoritical concepts
==========================================

polymorphism
------------

Imperative Programming
----------------------

Object Oriented Programming
---------------------------

Functional Programming
----------------------

expression
----------
is a combination of values constants variables
operators and functions that are interpreted according
to the particular rules of precedence and of association which computes
and then return another value  
expression containing functions may have side effect  
expression with side effects doesnot normally have referential transparency  

expression problem
------------------
the expression problem refers to the desire to implement an existing set of abstract
methods for and existing concrete class with needing to change the code that defines either  
normal oop language doesnt allow this  
some languages like Ruby and JS allows it by adding methods to existing concrete object
using wat is called as _monkey patching_  

side effects
------------
a function is said to have side effect if in addition to returing a result it
also modifies some state or have observable interaction with calling functions  
absence of side effects is necessart but not sufficient condition for referential transparency  

pure functions
--------------
the function always evaluate to the same result value given the same argument values  
evaluation of the result doesnot cause any observable side effects or output  

referential transparency
------------------------
an expression is said to be referential transparent if it can be replaced with its value
without changing the behavior of a program  
helps in improving programs through memoization, comman subexpression elimination and parallelization  
if all are pure function then the expression is referential transparent  


Monoid
------

Monad
-----
a srtcuture that represents computation  
http://www.intensivesystems.net/tutorials/monads_101.html  
james-iry.blogspot.com/2007/09/monads-are-elephants-part-1.html  
http://scabl.blogspot.in/2013/02/monads-in-scala-1.html  
in basic a monad contains to functions bind/flatMap/>>= and result/return/unit/single argument constructor or factory  

bind/... -> for a monad it takes applies a higher order function to each of the values in a monad (monadic value)  
unit/return/result/... -> takes a term of type A and turns it into a monad fo type M[A], this is
effectively saying it takes a value and return a monadic value  


the functions that are chained are called monadic function  
and the values that are returned are called monadic values  
a monad needs to follow 3 monadic laws  
join/flattern - ????  

Monadic zeros  

all monads are functors  

Functor
-------
for now look into scala treatement  
two functor laws - identity and composition  

higher order fucntions
----------------------
a function that takes a function as parameter and/or returns as function as result  

Lambda Calculus
---------------
http://www.ezresult.com/article/Lambda_calculus  
