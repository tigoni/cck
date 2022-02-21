---
layout: post 
title: "Types and TypeClasses in Haskell"
date: 2022-02-12 09:45:00 -0000
categories: haskell programming  
---
## Types
Haskell uses a static type system and this means every expression's type is known at compile time. Any incompatibility with types in evaluating expressions leads to compile time errors. Haskell also has type inference so we do not need to to explicitly write the type. It can infer this from the expression.


Common types are 
`Int`: Used for whole numbers and is bounded to a min and max value. On 32-bit machines, this bound is -2147483647 and 2147483647.
`Integer`: For whole numbers but unbounded.
`Float`: Floating point numbers with single precision.
`Double`: Floating point numbers with double precision.
`Bool`: A boolean type which can only have True or False values
`Char`: A character representation. 
`()`: An empty turple which can only have the a single value. `()`

By convention, all types are written starting with an Uppercase letter.
Functions in Haskell are also expressions and have types which can be declared as function signtures.

`sumOfInts :: Int -> Int -> Int`

The function has a type of `Int -> Int -> Int` which means it takes two integers as parameters and returns an integer.

### Types Variables
A type variable represents a generic type which can then be replaced with a concrete type when being used. It is used in writting general functions which can be applied to specific types in use. 
Functions that use type variables are called polymorphic functions. By convention, type variables are represented by lowercase single letters.

	sumTwoThings :: a -> a -> a
	sumTwoThings a a = a + a 

### Typeclasses
A typeclass is like an interface in imperative OOP languages. It defines behavior that will beexpected to be present in any type that becomes a member of it. 
For instance, `Eq` is a typeclass that provides an interface for testing equality in values that are members of it. If a type is member, it means that variables of that type can be compared for equality using functions present in the `Eq` typeclass. 

	checkIfPresent :: (Eq a) => a -> [a] -> Bool

In the above example, the function checks if a value `a` is present in a list `[a]` and returns true or false. The values to be used for `a` and `[a]` are constrained to be members of the `Eq` typeclass. This will allow the function to use the `==` function when checking for presence. The `(Eq a) => a ` part of the function declaration specifies this contraint.

Some of the basic typeclasses are:
`Eq`: Use for type that support equality
`Ord`: Use for types that support ordering
`Show`: Use for types that can be represented as strings.
`Read`: Use for types that can be read as strings and evaluted to the type.
`Enum`: Use for types that support sequentially ordered types
`Bounded`: Use for types that have a lower and an upper bound.
`Num`:  Use for types that have the property to act like numbers.
`Integral`: use for real numbers and Integral numbers.

