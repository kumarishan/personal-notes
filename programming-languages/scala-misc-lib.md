**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [Scala Miscellaneous libraries](#scala-miscellaneous-libraries)
	- [bijection](#bijection)
	- [spire](#spire)
	- [Scalaz](#scalaz)
	- [Shapeless](#shapeless)
	- [algebird](#algebird)
	- [spray](#spray)
	- [twirl](#twirl)

# Scala Miscellaneous libraries

## bijection
__twitter__  
invertible function to convert between types  

## spire
numeric library for scala intended to be generic fast and precise  
relies heavily on scala 2.10  

## Scalaz
extension to core Scala library for functional programming  

## Shapeless
polytypic programming in scala  

## algebird
abstract algebra for scala  

## spray
elegent high performance http for akka actors  

## twirl
scala template engine  

## eventsourced
add scalable actor state persistence and at-least once message delivery gaurantees to Akka
With Eventsourced, stateful actors
- persist received messages by appending them to a log (journal)
- project received messages to derive current state
- usually hold current state in memory (memory image)
- recover current (or past) state by replaying received messages (during normal application start or after crashes)
- never persist current state directly (except optional state snapshots for recovery time optimization)
only for 2.10.1/2