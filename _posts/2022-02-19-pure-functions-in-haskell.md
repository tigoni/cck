---
layout: post 
title: "Understanding Haskell Basics - Pt 1: Functions"
date: 2022-02-19 12:45:00 -0000
categories: haskell programming  
---
#### Understanding Haskell Basics
I am currently learning Haskell in readiness for writting Cardano smart in the Plutus language (which is based on Haskell). With a background of using OOP languages for a number of years, I am having to revisit and relearn fundamental programming concepts that I hope will make it easier in grasping why Haskell is so different from any language I have used before. This post is the first of a a series where I try to understand Haskell by looking at the fundamental computing principles which describe its features. 

From the Haskell website, the definition of the language is: **An advanced, purely functional language**. It also describes its main features as: statically typed, purely functional, type inference capability, concurrent, lazy and using a packages model.
For this post, I explore what purely functional really means and discuss what that means with compared to an OOP language.

Consider the following Java code:
```java
Integer result = 0;
Integer sum (Integer a, Integer b) {
    result = a + b;
}
```
The code snippet declares an integer variable `result` initialised to zero then defines a method `sum` that takes two Integer values, adds them and assigns the sum to `result`.
Two observations can be noted from the above code:
* We are using a collection of expressions (a, b, result) and operators to create statements that give instructions on *how* the sum of `a` and `b` is to be computed.
* The variable `result` is as used here, is in global scope. The method computes the sum of the arguments and assigns the result to that variable. In programming paradigms, this modification of a variable outside the local environment of the method is referred to as a *side-effect*.

The above approach is the norm in imperative programming languages where: (a) variables and statements are steps used to describe how the desired computation should be arrived at, and (b) expressions (variables, methods and operators) form statements are executed to change the state of a program.  
#### Whats's The Problem Here?
Using the earlier code snippet, suppose its part of a larger program and some other method later updates or resets the `result` variable?. Right there, we end up having a bug because the desired result is not what we expect. 

Another potential issue is what happens if the method is run concurrently by different threads? It's likely a race condition could result as each thread tries to update the mutable and shared variable.

If we were to write a test for the code above, how confident are we that the final result is what we are expecting. After all, we are not sure of what other operations are being performed on `result` pre or post the test. This means that our tests will need to account for such scenarios.
These are some of the issues a pure functional language such as Haskell addresses.
#### A Purely Functional Approach 
In Haskell, the focus is on *what to do* rather than *how to do it*. This means that the problem being solved by the program is decomposed into a series of functions (rather than statements) which are evaluated to get desired values. 

Generally, these functions have the following properties:
* A function called with the same arguments will always produce the same result regardless of how many times it is called. It has no knowledge of the external world.  
* The function will not have any side effects. This means that there is no mutation of local and non-local variables, reference arguments and input/output streams.

Here's a code snippet of the earlier method written in Haskell.
```haskell
sum :: Int -> Int -> Int
sum a b = a + b
```
Now we revisit the issues we disussed with our code snippet written using an imperative language and finally explore the benefits of a functional approach.

First, functions become easier to understand and test because we know that for every given input, the output will always be the same. In addition, since our function cannot modify any external state, it becomes much easier to write a self contained test without worrying of mocks and such.

Second, because functions will not access and/or modify any variables outside their environment, any threads running the function concurrently will not have undesired effects and this means functions are thread safe. In addition, this property allows for parallel computation since functions are self contained.

While the benefits of a purely functional approach are clear, it does come with some level of difficulty in implementing solutions, more so, for someone coming from an imperative language and is used to a certain way of doing things. 
For instance, there are no loops and recursion is the way to iterate over items. Adjusting to a recursive style of programming has taken me some time. In addition, the whole idea of writting a program entirely composed of functions is yet to sink in. 

In the other posts of this series, I will continue discussing the general benefits of a functional approach in the context of a more specific topic and hopefully we all get to learn.






