[[_ Real World Haskell]]

https://book.realworldhaskell.org/read/types-and-functions.html


**every expression and function in Haskell has a type**:
- `True :: Bool`
- `"Foo"::String`

>[!info] Type
>the type of a value indicates that it **shares** certain **properties** (concatenate lists, add numbers) with other values of the same type

 >[!info] abstraction
 >The benefit of introducing **abstraction** is that it lets us forget or ignore low-level details.
 >If I know that a value in my program is a string, I don't have to know the intimate details of how strings are implemented.
 >**Haskell's type system allows us to think at a very abstract level**
 
 
# Haskell's type system
## strong
- The type system guarantees that a program cannot contain cerain kinds of errors (int used like function -> Haskell's compiler generates an error)
- no automatic coercion/casting/conversion

**benefit** strong typing catches  bugs in our code before they can case problems


## static
The compiler knows the type of every value and expression at compile time, before any code is executed

## inferred
Finally, a Haskell compiler can automatically deduce the types of almost all expressions in a program. This process is known as _type inference_. Haskell allows us to explicitly declare the type of any value, but the presence of type inference means that this is almost always optional, not something we are required to do.


---
# List, tuples

## lists, tuples
### list
`head [1,2,3]` -> `1`
`tail [1,2,3]` -> `[2,3]`
**list type** is ==polymorphic== because the values in a list can have any type


**Haskell tuples aren't immutable lists**

----
# Functions

## Function application has higher precedence than using operators

==function application is left associative==
	`a b c d` is equivalent to `(((a b) c) d)`
so
```haskell
ghci> head (drop 4 "azerty")
't'
```

> 
> *function_name*  `arg1 arg2 ...`   =   *function body*
> 

## load a file to ghci
- `:load fileName.hs`
- `:cd /some_folder` > `:l file.hs`
- `:l someFolder/file.hs`

## function is expression
**Function** is **a single expression**, not a sequence of statements (it has no *return* keyword)

## ` = ` 
- this operator represents "**meaning**" 
- `x = 10` the name `x` is defined to be the value of the expression `10`
- **variable** provides a way to give a name to an expression
	- its value **does not change**
	- we can always use the name of the variable instead of writing out the expression
	- in *imperative* languages *variable* is a way of identifying a *memory location*
```haskell
-- this code results in an error
x = 10
x = 11
-- we cannot assign a value to `x` twice
```


---
## Conditional evaluation
```haskell
myDrop n xs = if n <=  0 || null xs
			then xs
			else myDrop (n - 1) (tail xs)
```


-----
## Evaluation

### lazy evaluation - non-strict evaluation
nonrecursive function
```haskell
isOdd n = mod n 2 == 1
```

### `isOdd (1+2)`
#### *strict* evaluation
==the arguments to a function are evaluated before the function is applied==
1. evaluate the subexpression `1+2` --> `3`
2. apply `isOdd`  with `n` bound to `3`
3. evaluate `mod 3 2`
4. evaluate `1 == 1`
5. return `true`

#### *non-strict* evaluation - Haskell
- `1+2` is not reduce to `3` -- we create a *promise* that when the value of the expression `isOdd (1 + 2)` is needed, we will be able to compute it
- 







