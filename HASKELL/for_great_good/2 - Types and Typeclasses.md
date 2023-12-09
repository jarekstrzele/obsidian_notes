[[0 - Haskell intro]]


---
# Types and TypeClasses

Haskell has a [[static type |  static type system]].

Everything in Haskell has a type, so the compiler can reason quite a lot about your program before compiling it.

Haskell has ==type  inference== - if we write a number, we don't have to tel Haskell it's a number. In can ==infer== that on its own, so we don't have to explicityly write out the types of our functions and expressions to get thing done.

> ==a type== is a kind of label that every expression has. It tells us in which category of things that expression fits. The expression `True` is a boolean, `"hello"` is a string, etc.

## to examine types
`:t` command which, followed by any valid expresiion
```bash
ghci> :t 'a'  
'a' :: Char  
ghci> :t True  
True :: Bool  
ghci> :t "HELLO!"  
"HELLO!" :: [Char]  
ghci> :t (True, 'a')  
(True, 'a') :: (Bool, Char)  
ghci> :t 4 == 5  
4 == 5 :: Bool
```

`::` is read as "has type of"
Types are always denoted with the first letter in capital case: `Bool  True  Char ...`
`[Char]` a list of characters

## Functions
Functions also have types
==a type declaration==
`removeNonUppercase :: [Char] -> [Char]  `

==a function definition==
`removeNonUppercase st = [ c | c <- st, c 'elem' ['A'..'Z']] `

```bash
addThree :: Int -> Int -> Int -> Int  
addThree x y z = x + y + z
```
the return type is the last item in the declartation and the parameters are the first three (you can write `Int, Int, Int -> Int`)

## some common types
`Int` whole numbers, is bounded (has a min and max value)
`Integer` whole numer, is NOT bounded
`Float`  a real floating point with single precision
`Double` a real floating point with double presicion
`Bool`
`Char`
TYPLES - a type depends on their length and the types of their components


## Type variables
```shell
ghci> :t head  
head :: [a] -> a
```
`head` takes a list of any type and returns the first element
`a` can be of any type

>Functions that have type variables are called ==polymorphic functions==

```shell
ghci> :t fst  
fst :: (a, b) -> a  
```
`a` and `b` are different type variables, but they don't have to be different types

---

## TYPECLASSES 101

> ==a typeclass== is a sort of interface that defines some behavior.
> If a type is a part of a typeclass, that means that it supports and implements the behavior the typeclass describes.
> THey are NOT classes like in OOP!

```shell
ghci> :t (==)  
(==) :: (Eq a) => a -> a -> Bool  
```
the `==` operator is a function (*infix* function, so if we want to examine its type, pass it to anothe function or call it as a prefix finction, we have to surround it in parentheses)

**class constraint** `=> ...`
`(Eq a) => a -> a -> Bool`the equality function takes any two values that are of the same type and returns a `Bool`. The type of those two values must be a member of the `Eq` class

### Soma basic typeclasses
#### `Eq`
is used for types that support equality testing. The funtions its members implement are `==` and `/=`.

#### `Ord` 
is for types that have an ordering (`< > <= >= `)

#### `Show` 
can be presented as strings. The most used function that deals with `Show` typeclass is `show`. It takes a value whose type is a memeber of `Show` and presents it to us as a stirng
```haskell
ghci> show 3  
"3"  
ghci> show 5.334  
"5.334"  
ghci> show True  
"True"  
```


#### `Read` 
is sort of the opposite typeclass of `Show`. The `read` function takes a string and returns a type which is a member of `Read`
```haskell
ghci> read "True" || False  
True  
ghci> read "8.2" + 3.8  
12.0  
ghci> read "5" - 2  
3  
ghci> read "[1,2,3,4]" ++ [3]  
[1,2,3,4,3] 
```

but `read "4"` generates an error, you have to write `read "5" :: Int` or `read "5" :: Float` ...


#### `Enum`
- members are sequentially ordered types - they can be enumarated
- members have defined successors `succ` and predecesors `pred`
- types in this class `()  Bool Char Orering, Int, Float ...`


#### `Bounded`
members have upper and a lower boudn
`minBound :: Int` -2147483648
`maxBound :: Bool` True


#### `Num` (real + integra numbers)

- is a numeric typeclass
- its members have the property of being able to act like numbers
```bash
ghi> :t 20
20 :: (Num t) => y
```


#### `Integral` and `Floating`
```haskell
fromIntegral :: (Num b, Integral) => a -> b
```













