---
layout: post 
title: "Static Typing and Type Inference in Haskell"
date: 2022-02-26 11:50:00 -0000
categories: haskell programming  
---

### Types
In computing,variables, expressions and functions are evaluated to values to arrive at a desired result. A type system in programming provides for the categorization of these data values into 'groups' such that consistency rules can be imposed on how the values are used later on in the program. The general idea is to reduce the occurence of bugs that would arise when values of different types are mixed in the wrong way.

A programming language's type checker uses a defined rule set to enforce rules on how types are used on values, data and other types thoughout the program and ensures that no inconsistencies arise. Type checking can be done either at compile time (also called static typing) or at runtime.
### Static Typing
Haskell being statically typed means that type checking is done when the program is compiled by examining the source code. The type checker will ensure that:
Every value has a type and that value is not used in a way that will cause type inconsistencies. With dynamic typing, the type of a variable will be determined by the value assigned to it and the variable can take on many different types during program execution. Such a program will still compile even if these type errors will result in errors at runtime. Static type checking ensures that with type inconsistencies are caught at during the complitation stage.

In Haskell, all values (meaning all variables, expressions and functions that evaluate to a value) have a type. Before a value can be used, a type has to be assigned and that type cannot be changed otherwise a compilation error is shown.

Apart from making programs type-safe, static typing has the benefit of producing more efficient code. As a result of the  compiler knowing all the types before runtime, it is able to generate optimized machine code which runs faster. 

### Type Inference
Unlike a language like Java or C++, Haskell is able to determine the type of expressions without it being explicitly stated by the programmer. 
For example: when declaring a varible, we can do this
```haskell
> let x = 12.783
```
From this code, Haskell is able to deduce that varible x should be of type `Float`. Similarly, the type signature of a function can be determined automatically by haskell. 
```haskell
> sum a b = a + b
> :t sum
>  sum :: Num a => a -> a -> a
```
However, by convention, we should always provide type signatures for variables and functions especially in larger programs to provide clarity and documentation.