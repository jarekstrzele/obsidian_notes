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


## data type
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


## Math
```haskell

main = do
  print ( 2 + 2 )  -- 4
  print ( 4 - 4 )  -- 0
  print ( 2 * 2 )  -- 4
  print (4 / 2)    -- 2.0
  print ( 2 ** 4 ) -- 16.0

```


```kotlin
main = do
  print ( sqrt 81 )      -- 9.0
  print ( round 5.6 )    -
  print ( round 5.4 ) 
  print ( floor 5.679)
  -- print ( 5 `mod` 4)
  print ( mod 5 4 )
  print (rem 5 4)
```














