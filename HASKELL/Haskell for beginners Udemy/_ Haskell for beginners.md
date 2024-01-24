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























