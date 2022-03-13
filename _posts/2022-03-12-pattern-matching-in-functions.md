---
layout: post 
title: "Pattern Matching In Functions"
date: 2022-03-12 14:41:00 -0000
categories: haskell programming  
---

#### What is It
Pattern matching is a mechanism where values are matched against a pattern and when a successful matche is found, the value is bound to variables in the matching pattern. Any data type can be pattern matched and its values bound to those specific patterns. 

Pattern matching is usefull in several ways. It helps when want to have different functions for different inputs. It also allows us to unpack and expose contents in our data for instance in the case of matching  data constructors.

#### Basic Pattern Matching
Suppose we have a function `numberToText`. It takes an Int value and outputs a string representation of that value.
```Haskell
numToText :: Int -> String
numToText 1 = "one"
numToText 2 = "Two"
numToText _ = "Other Number"
```

When the function is called with a value eg. `numToText 2`, Haskell compares the argument value `2` to the patterns defined for the function. The pattern matching starts from the top to the bottom of the function definition. If the value (`2`) matches any of them, the corresponding function will be called. 

Notice the `_` used in the last pattern. This is a convention used to catch anything else that fails to match the previous patterns. It can be seen as an 'anything-else' case. From the above example, any value that is not 1 or 2 will be matched to the last pattern and the output will be "Other Number". 
This implies that pattern ordering matters because if we put the last pattern as the first, then all function calls would be match the value to the `_` pattern and use that for evaluation. Therefore as a general rule, the 'everything-else' pattern should be the last one when defining patterns. 

In a situation where we do not specify all the possible patterns and a function call fails to match any of the listed patterns, an exception is shown as: 
```haskell
*** Exception: <interactive>:(3,1)-(5,15): Non-exhaustive patterns in function numToText
```

#### Pattern Matching with Data Constructors
When using custom data types, pattern matching is useful bacause it allows us to expose the contents of the data and specify the behavior to be applied based on that data.

```haskell

type AuthorCountry = String
type Title = String

data Book = TextBook Title AuthorCountry

hasAuthorCountry :: Book -> Bool
hasAuthorCountry (TextBook title "KE")  = True
hasAuthorCountry (TextBook title "")  = False
```

In the above example, we can check the values in a data contructor and use patterns to determine what happens when a matching value is found. Therefore we are able to unpack the data values in a `Book` and vary behavior based on the values found.