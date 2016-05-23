---
layout : post
title : 'Introduction to Haskell'
subtitle : 'Scribble pad for learning'
date : 2016-05-21 00:00:00
categories : [tool]
---
- Created in 1987 by enthusiasts to help increase the productivity and accuracy
- Pure Functional Language
  - Functions are first class member, that is functions can be used like any other values.
  - Expressions never have "*side-effects*"
  - Functions will always return same output for same input.
  - *referential transparency* - No Mutation ! this comes handy when working with concurrency.
- Lazy
  - Haskell expressions are not evaluated until their results are needed.
  - Helps in working with infinite data structures
  - *wholemeal programming* - a more compositional programming style
- Statically typed
  - Apart from being Statically typed, haskell is an expressive language (that makes it different form java, c++)
- Concise
  - A 5M lines of code in Java can be written in 1M lines in Haskell
- Speed
  - As fast as ( sometimes more ) Java, C++
    - directly to native
    - abstraction provides multicore & parallel processing.

## Installing
- I have installed it using stack - look at [this](https://www.youtube.com/watch?v=sRonIB8ZStw) video


### Types
- type of a method say

```search x [] = False``` would be ``` Eq a => a [a] -> Bool ```

> here Eq a is a constraint ( like generics in Java)

---

let's say you have the following code

```
    search x [] = False
    search x (y:ys) =
      if x == y
        then True
        else search x ys
```
if you run this on the ghci

``` :t search ```

it will return something like ::

``` Eq a => a [a] -> Bool ```

Now let's re-write the code


```
search x [] = False
search x  l =
	if x < y
		then search x ys1
		else if x > y
			then search x ys2
			else True
	where
		ys1 = take len l
		(y:ys2) = drop len l
		len = length l `div` 2
```

  if you run this on the ghci
  ``` :t search ```
  it will return something like ::

``` Ord a => a [a] -> Bool ```

> Notice how Haskell has implicitly understood the type and constraint of the function
