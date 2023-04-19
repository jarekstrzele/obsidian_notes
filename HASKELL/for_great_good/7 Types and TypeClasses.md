http://learnyouahaskell.com/making-our-own-types-and-typeclasses


# Algebraic data types
in the standard library `Bool` is  define:
`data Bool = False | True` 
- the Bool type can have a value of True or False. 
- Both the type name and the value constructors have to be capital cased.

`data` - define a new data type
`Bool` denotes the type
` = ` **value constructor** (specify different values that this type can have)
` | ` or



#### ` type = value constructor`


## examples
### to represent a shape in Haskell
- by tuple  `(43, 50, 10.4)` (x,y,radius)
- better way by making your own data type (shape can be Circle or Rectangle only)
```haskell

data Shape = Circle Float Float Float | Rectangle Float Float Float Float
```

`Circle` value contructor has three fields which takes  floats
(fileds are parameters)
> value constructor is a function that returns a value of data type

```haskell
ghci> :t Circle  
Circle :: Float -> Float -> Float -> Shape  
ghci> :t Rectangle  
Rectangle :: Float -> Float -> Float -> Float -> Shape
```
```haskell
surface :: Shape -> Float
surface (Circle _ _ r) = pi * r^2
surface (Rectangle x1 y1 x2 y2) = (abs $ x2-x1 ) * (abs $ y2 - y1)

ghci> surface $ Circle 10 20 10
314.15927

```


> [!important] show
>  Remember, when we try to print a value out in the prompt, Haskell first runs the show function to get the string representation of our value and then it prints that out to the terminal.

```haskell
data Shape = Circle Float Float Float | Rectangle Float Float Float Float deriving (Show)
```










