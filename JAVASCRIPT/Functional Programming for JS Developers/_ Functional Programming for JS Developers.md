#udemy #artech_learning

-------





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
- the functions defined here are independend and reusable
- no reliance  on an abstract object being passed arpund
- much easier to unit test
- `map` to avoid for loop
- no mutable variables
- anonymous arrow functions





