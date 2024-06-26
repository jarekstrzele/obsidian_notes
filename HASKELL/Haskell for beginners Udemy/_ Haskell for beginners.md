#haskell #udemy 


---
env: replit.com



---
# `main` function

> in Haskel everything goes inside the MAIN FUNCTION

```haskell
-- MAIN FUNCTION in one Line
main = putStrLn "Hello World"
```

If you want your `main` function to include multiple expressions or multiple lines, then you have to use the `do` statement
```haskell

-- Haskell will be able to determine the type of someVar
someVar = "global variable" 

-- data types
neeName :: String
neeName = "Adam"

main = do
  let name = "Henry"
  let age = 36

  putStrLn "Hello world"
  putStrLn ("Hello " ++ name)
  print age
  putStrLn( "I'm " ++ show age ++ " years old")  
```

`let <name>` creates a variable inside function (e.g. `main`)
`<name>` global variable outside the function
`print` use is when you are printing out numbers, list, tuples, records
`putStrLn` use to print out string

##### *cameCase* naming

>[!danger] important
>Haskell is an immutable language and you can't use the same variable name more than once


# data type
```haskell
age :: Int
age = 16

height :: Double
height = 1.2

aBool : Bool
aBool = True

aChar :: Char
aChar = 'a'

main :: IO()
main = putStrLn "Hello world!"









```


# Math
```haskell

main = do
  print ( 2 + 2 )  -- 4
  print ( 4 - 4 )  -- 0
  print ( 2 * 2 )  -- 4
  print (4 / 2)    -- 2.0
  print ( 2 ** 4 ) -- 16.0

```


```haskell
main = do
  print ( sqrt 81 )      -- 9.0
  print ( round 5.6 )    -- 6
  print ( round 5.4 )    -- 5
  print ( floor 5.679)   -- 5
  -- print ( 5 `mod` 4) 
  print ( mod 5 4 )      -- 1, wynik zawsze nieujemny
  print (rem 5 4)        -- 1
```

```haskell
main = do
  print( pi ) -- 3.141592653589793
  -- print ( exp 1)
  print $ exp 1 -- 2.718281828459045
  print $ log (exp 1) -- 1.0
  print $ sin 0 -- 0.0
  print $ cos 0 -- 1.0
  print $ tan 0  -- 0.0

```


----
# Modules

## List Module

to use that module:
`import Data.List`

```haskell
import Data.List


main = do
  print(intersperse '.' "SPEW") 
  -- "S.P.E.W"
  
  print(intercalate " " ["Art", "Of", "War"]) 
  -- "Art Of War"
  
  print(splitAt 5 "UdemyCourses") 
  -- ("Udemy","Courses")
  
  print(sort [84,1,4,8,56,3]) 
  -- [1,3,4,8,56,84]
  
  print(sort ["zebra", "apple", "dolphin"]) 
  -- ["apple","dolphin","zebra"]
```















