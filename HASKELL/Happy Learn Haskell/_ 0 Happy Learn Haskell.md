http://www.happylearnhaskelltutorial.com/1/how_to_enjoy_learning.html#s1

[[3 Types as Jigsaw Pieces]]
[[4 the Main Road]]
[[5 Function Magic]]


>[!info] **VALUES**
>- a value in  Haskell is any data
>- e.g. "step"
>- all values have a type

>[!info] **Types**
>- a type is a name for a set of group of values that are similar
>- e.g. Integer - the type for representing values like `5`, `32`, ...
>- `5 :: Integer`
>- Haskell lets us  make our own type
>- Types are important:
>	- decide how the pieces of your program can fix together
>	- which values are allowed to go where

>[!infor] **DEFINITIONS
> ` = ` this symbol tells Haskel that we want it to remember a name for an **expression**
>`name = expression` 
>the symbol ` = `  **binds** (relates) the name  or pattern on the left of it with the expression on the right of it
>`five = 5` name `five` means the value `5`
>

>[!info] **FUNCTIONS**
>- a function is a relation between one type and another type
>- it is used in expressions with values
>- a function is itself a value
>- functions in Haskell **are not sets of steps** for the computer to foloww

## First program
```haskell
main = putStrLn "Polly wants a cracker"
```
- this is an expression
	- starts with `main`
	- involves a function being applied to a value

**the whole** line is called  a definition - it is made of three pieces:
1. the variable or term `name`
2. the ` = ` symbol
3. an expression

>It’s important to realise that the “ ` = `” symbol:
>	- **doesn’t mean we’re “setting” anything here**, or “putting” anything into anything else. 
>	- we **use it to name expressions, it's all**. 
>	- **The name does not “contain” the value**, so we cannot re-define the same name at a different point in our program, or change the name’s “content” or definition after it has been defined.

### `main`
- this is the term/variable.
- every program must defin `main`
	- it is evaluated and 
	- executed by Haskell to run your progam
- if you named it `pain` instead of `main` - the program would not work
- it is **the entry point** 
- it is **a value** and **input/output** action (**IO** action for short)

>[!info] EXPRESSIONs
>- Expression share how we express values
>they have a type, too












