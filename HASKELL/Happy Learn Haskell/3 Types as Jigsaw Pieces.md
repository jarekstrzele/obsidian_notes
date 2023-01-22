[[_ 0 Happy Learn Haskell]]

----
### data
**data** is like a magical puzzle piece (it can shrink and grow) as needed to fit together

### type
**types** (simple types) would be the shapes of the puzzle pieces
#### type annotations / type signature
`m :: String`

### definition
`m = "Dolly wants a cracker"`
you define a name `m` as being the String that is literally `Dolly wants a cracker`

### types for functions
`putStrLn :: String -> IO()`:
- `putStrLn` has type `String` to `IO()` action 
- `putStrLn` ia a function from `String` value to `IO` action

`putStrLn "Dolly wants a cracker" :: IO()`
`putStrLn ("Dolly wants a cracker" :: String) :: IO() `
`putStrLn m :: IO()`
**type inference** - Haskell can works out the types from the context

```haskell
m :: String
m = "Dolly wants wants a cracker"

main :: IO()
main = putStrLn m
```

### function
>[!info] FUNTION
>a function is:
>- a value that expreses
>	- a particular relationship between:
>		- the values of types
>it relates one set of values to another set of values 

`putStrLn`  relates `String` values to particular kinds of `IO actions`


## `main`
#haskell/main
- Haskell requires that `main` is an `IO` action
- its type is written `IO()` -- `IO` action that returns **nothing of interest** (but does some action when executed)
- value **Unit**  is a nothing of interes and it's written `()`
- 












