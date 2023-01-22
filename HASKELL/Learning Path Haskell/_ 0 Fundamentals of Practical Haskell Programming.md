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
--- semantically, this program binds the name `main` to the expression 
```

`putStrLn` the func that takes a single artg of type string and eveluates to an action that when executable string s the terminal and produce no result

in the terminal:
`stack runghc Program.hs`
`runghc` it is an interpreter 

`main::IO()` this means `main` is a finction that evaluates to an action which produces no value

```haskell
main :: IO ()

main = do
    content <- readFile "nums.txt"
    putStrLn content
```

`do` is pronounce *from the code* or *drawn form*
*content is drawn from read file applied to nums.txt*

#haskell/print
`print` can be applied to any value that implements the Show type class and is typically used to display a representation of a value for diagnostic purposes 

`putStrLn` is used to output a string folow ya newline character


```haskell
readInts :: String -> [Int]
readInts s = let ws = words s in map read ws

minMax :: Ord a => [a] -> Maybe (a, a)
minMax (h : t) = Just $ foldr
    (\x (min, max) -> (if x < min then x else min, if x > max then x else max))
    (h, h)
    t
minMax _ = Nothing

main :: IO ()
main = do
    content <- readFile "nums.txt"
    let values = readInts content
        count = length values
        total = sum values
        mean = fromIntegral total / fromIntegral count
        range = minMax values
    print count
    print total
    print mean
    print range
```


------------------
# Whitespace, Layout and Scoping
- Haskell is a white space sensitive language
- Haskell is an "off-side rule" language
- enforced by compiler
- rules are usually intuitive
- used in `where`, `let`, `do`, and `case ... of` constructs

```haskell
main =
	let
		x = 5
		y = 6
	in print (x + y)
```

`stack ghc -- --fno-code fileName.hs` compile the file but not produce any executable file; it checks only the syntactic correctness

```haskell
f = do
	a
	b
	c
g = do a
	   b
	   c

a:: IO()
a = indefined; b = udefined; c = undefined
main = undefined

	   
```


```haskell
f x y = a + b
	where
		a = x
		b = y

g x y = a + b
	where x = b
		  y = b
		  
```


```haskell
f x = case x of p0 -> a
				p1 -> b

g x = case x of
		p0 -> a
		p1 -> b
```


```haskell
main = let { x = 5; y= 6} in print (x + y)
```


-----
# GHCI
#ghci

**ghc** stands for "Glasgow Haskell Compiler"
**ghci** is "GLasgow Haskell Compiler Interactive"

`:!` you can use bash command
`:!dir`

### `it`
```ghci
ghci> it

<interactive>:3:1: error:
    * Variable not in scope: it
    * Perhaps you meant `id' (imported from Prelude)
ghci> x = 1
ghci> y = 11
ghci> x+y
12
ghci> it
12
ghci>
```

`:type <value>` 
`:kind <class>`

```ghci
ghci> :t x
x :: Num a => a
ghci> :t Num

<interactive>:1:1: error:
    * Illegal term-level use of the type constructor `Num'
        imported from `Prelude' (and originally defined in `GHC.Num')
    * In the expression: Num
ghci> :kind Num
Num :: * -> Constraint
```

`prettyPrint`
`:run`
`:main`

### debugging with 
`> echo %APPDATA%`

GHCI can privde powerful insights into the *runtime* behaviour of programs

`:break <name>` -> `:break minMax` (where `minMax is a function defined in a file`)
	`:sprint ...`
	`:continue`
	`:list`
	`:show breaks`
	`:show bindings`
	`:abondon`


----
# Values and Expressions

## values of primitive types
- Char
- Integer
- Int
- Float, Double
- almost everything else is defined in terms of these

```haskell
ghci> a :: Int ; a = 1234
ghci> :sprint a
a = _  -- a is not yet eveluated
ghci> :type a
a :: Int
ghci> a
1234
ghci> :sprint a
a = 1234
ghci>
```

```haskell
ghci> b :: Integer ;  b = 2 ^ 70
ghci> :sprint b
b = _
ghci> b
1180591620717411303424
ghci> :sprint b
b = 1180591620717411303424
ghci> a :: Int ; a = 2 ^ 70
ghci> a
0
```


## Functions as values
`import Data.List` - this gives us access to the intercalated function
```haskell
ghci> intercalate ":" ["/path/to/dir0", "/path/to/dir1"]
"/path/to/dir0:/path/to/dir1"
ghci> formatList s e sep xs = s ++ (intercalate sep(map show xs)) ++ e
ghci> formatList "(" ")" ", " [1,2,3,4]
"(1, 2, 3, 4)"
ghci> formatList "(" ")" "- " [1,2,3,4]
"(1- 2- 3- 4)"
ghci>
ghci> f = let s = "hello world" in putStrLn $ "(" ++ s ++ ")"
ghci> f
(hello world)

-----
ghci> addTen x = x  + 10
ghci> doubleIt x = x * 2
ghci> addTen 5
15
-- COMPOSE
ghci> addTen (doubleIt 5)
20
ghci> addTen $ doubleIt 5
20
ghci> (addTen . doubleIt) 5
20

ghci> (show . addTen . doubleIt) 5
"20"
ghci> show . addTen . doubleIt $ 5
"20"
```

## Function application


## Function composition


## Anonymous functions


## Infix functions, sections and partial application







