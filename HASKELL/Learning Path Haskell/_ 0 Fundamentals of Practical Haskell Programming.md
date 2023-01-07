#udemy #haskell  #cook_richard

[[1 Exploring Haskell]]
[[2 Haskell in Depth]]

----
# Stack

https://docs.haskellstack.org/en/stable/

>[!info] The Haskell Tool Stack
>It is a cross-platform program for developing Haskell projects

# install on Windows

verify 
```powershell
C:\Users\jaros>where stack
C:\ghcup\bin\stack.exe
```

create a stack project
```powershell
PS C:\Users\jaros\Desktop\Prog> stack new first-stack-project
Downloading template "new-template" to create project "first-stack-project" in first-stack-project\ ...


```

- it creates a new directory that contains all the files needed to start a project correctly, using a default template
- go to that folder
- `stack build` - will build the template project and create an executable named `first-stack-project-exe.exe`
- `stack exec first-stack-project-exe` will run (execute) the built executable


--------------
# Install on Linux



----

# Fundamentals of Practical Haskell Programming

### FP - Functional Programming
### PL - Programming Language


## FP Way
- it is an alternative model of computation
- treats computation as the evaluation of mathematical functions
- is declarative, emphasizing the "what" over the "how"

### FP programs:
- contain expressions and declarations
- avoid chaging globale state
- avoid mutating data
- avoid looping and, instead, employ recursin or higher-order abstractions

**traversal** (a.k.a. `mapping`) the process of iterating over elements and performing an action on each item
```haskell
main = print $ map (+ 10) [1,2,3]
```

**reduction**(a.k.a. `floding`)the process of iterating over a collection of elements in order to produce some kind of summaryy such as a total
```haskell
main = print $ foldr (+) 0 [1,2,3]
```

**filtering** iterate over a collection of elements and extract the subser for which some predicate holds true
```haskell
main = print $ filter (> 3) [1,2,3,4,5,6]
```

**compostion** join two or more function together to produce a bigger function
```haskell
f x = x + 10
g x = x * x

main = print $ map (g . f) [1,2,3]
```


----
# The Haskell Way

## FP Features of Haskell
- functions are first-class values
- higher-order functions can be elegantly expressed
- Haskell does not support standard loop control flow
- Haskell is about expressions and declarations

```haskell
main :: IO ()
addBrackets :: [Char] -> [Char]
addBrackets s = "[" ++ s ++ "]"

result :: [[Char]]
result = map addBrackets [ "one", "two", "three"]

main = print result
```

`stack runghc fileName.hs` - this takes a Haskell source file and runs it as if it is an interpreter and so it takes the code and executes it without going through compilation past first 

```powershell
> stack runghc .\app\Main.hs
["[one]","[two]","[three]"]
```


## Pure Functions Everywhere
- all functions are pure in Haskell
- Not a requirement for an FP PL
- Core to generating efficient code

## Non-strict evaluation
- function args are not eveluatated unless they'ar actually used
- args are evaluated on demand and the results will memorized for future use
- that lazy evalutation allow us to build our own control structures

```haskell
main :: IO ()
myIf :: Bool -> p -> p -> p
myIf True thenFunc elseFunc = thenFunc
myIf False thenFunc elseFunc = elseFunc

main =
    let x = 5
    in print $ myIf (x==5) "is five" "is not five"
```


## Strong and Static Type System
- catch as many potential defects at compile time as possible
- generate the most efficient code as possible
- types are deleted at compile time


----
# First Haskell Programs

```haskell
-- main is putStrLn hello world
main = putStrLn "Hello world"
--- semanthis program binds 
```








