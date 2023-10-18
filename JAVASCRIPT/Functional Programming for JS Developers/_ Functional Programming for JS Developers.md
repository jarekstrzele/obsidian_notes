#udemy #artech_learning

-------
IMPERATIVE STYLE
- read top-to-bottom
- tell computer step by step instructions
- each step depends on knowing where 




----

# Intro:
What is functional programming?
Recursion
Currying
Map
Reduce
Filter
Composition
Applying function techniques today



----
# Why functional programming
Here are some key reasons why JavaScript developers should consider learning functional programming:

1. ==Readable and expressive== code: FP promotes writing small, pure functions that are easy to understand and reason about. This makes the code more readable and expressive, which in turn facilitates better communication between team members.
    
2. ==Reusability and modularity==: Functional programming encourages breaking down problems into smaller functions that can be easily reused and combined. This modularity helps developers create reusable, composable code that can be easily maintained and scaled.
    
3. ==Immutability and predictability==: FP focuses on immutability, which means that once data is created, it cannot be changed. This approach reduces bugs related to shared mutable state and makes the code more predictable, leading to fewer unintended side effects.
    
4. ==Easier debugging and testing==: Since functional code is composed of small, independent functions, it is generally easier to test and debug. Pure functions are particularly advantageous because they depend only on their input, making it easier to identify issues and write tests.
    
5. ==Concurrency and parallelism==: FP's emphasis on immutability and avoiding side effects makes it a natural fit for concurrent and parallel programming. In an increasingly multi-core and distributed computing world, functional programming can help developers better leverage these resources for improved performance.
    
6. ==Better performance==: While JavaScript is not a purely functional language, incorporating FP principles can lead to performance optimizations like lazy evaluation and memoization, which can help improve the overall performance of your applications.
    
7. ==Growing demand==: There is a growing demand for functional programming skills in the industry, as more companies recognize the benefits of using FP principles in their codebases. Learning functional programming can help you stay ahead of the curve and make you more marketable as a developer.
    

In **summary**, learning functional programming can help JavaScript developers write:
- cleaner, 
- more efficient, and 
- maintainable code, 
- while also enhancing their skills and m

--------
# IMPERATIVE STYLE
- read top-to-bottom
- tell computer step by step instructions
- each step depends on knowing where you are in the process
- statements change the state of the application

**example**
button -> onclick -> prompt to take a string from user > function to make uppercase string -> alert to display the result
- variables defined in the global scope, outside function
- interdependent functions
- values being passed around and redefined
- mixed: native JS  and DOM methods
- unclear what is happening outside the script
- funcion names being repeated

----
# OOP
- data treated as objects to be passed around
- use defined methods to manipulate objects
- passing messages
- hiding and sharing  properties
- composition
- inheritance
- 

the same example:
- improved focus on encapsulation of functionality
- ability  to "use strict" in a limited scope
- methods used by a given object are attached to that object
- methods are defined on the prototype to conserve memory
- new `addEventListener` is more versatile


----
# Functional Style
- take advantage of functions as first-class object
- don't change external values or state while executing function
- describe the problem or solution

the same example
- code is more concise
- the functions defined here are independent and reusable
- no reliance  on an abstract object being passed around
- much easier to unit test
- `map` to avoid for loop
- no mutable variables
- anonymous arrow functions


# Pure Functions
#pure_function
- don't rely on the state of the code they are called from
- don't create side effects that alter variables outside themselves
- only one result for any given set of arguments
- 

**don't rely on the state of the code they are called from**
```js
// an impure function may rely on global or externally deined values
const external = [1,2,3] ;
const impure = value => {
  let result = value + external.length; //external.length  
  external.push(result) ;
  return result ;
};

console.log(impure(4)) ; //  --> 7
console.log(impure(4)) ;  // --> 8
```



**don't create side effects that alter variables outside themselves**
-- an impure function may make changes to values outside of itself


**only one result for any given set of arguments**
-- an impure function may not always return the same result with the same input

```js

const external = [1,2,3] ;
const pure = (value, arr) => {
  let result = value + arr.length; //external.length 
  return result ;
};

console.log(pure(4, external)) ; // -> 7
console.log(pure(4, external)) ; // -> 7
external.push(4) ;
console.log(pure(4, external)) ; // -> 8

```
``
==Mutable values can change result, even with a pure function==


ADVANTAGES OF PUR FUNCTIONS
- results are easy to reproduce and test
- can be called in parallel  without altering results
- allow for memoization
- potential for lazy evaluation
- 


---
# Higher order functions

in JS
- the type of a function is Object
- functions can be assigned to a variable as a value
- functions can be passed to another function as an argument
- functions can be returned by another function as a result


>[!info] HOF
>- a function that takes a function as an argument
>- a function that returns a function as result
>- a function that both accepts and returns functions














