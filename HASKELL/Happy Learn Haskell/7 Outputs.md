```haskell
-- both types must be the same, 
-- so this will be fine: 
goodNumber = (3 :: Integer) + (5 :: Integer) 

-- this would cause a type error 
willNotWork = (3 :: Int) + (5 :: Integer)
```


```bash
*Main> :t (+)
(+) :: Num a => a -> a -> a
```
`Num a =>` "a is constrained to types which are instances of the `Num` typeclass"
`a` any typa

# Typeclass

#haskell/typeclass
>[!important] Typeclass
>- it is not a concrete type like `Integer, Int, String`,
>- it is a way of tagging **many** types
>- we can have functions or values that work with many similar types that do similar things, but that are actually different.

```haskell
-- a small int 5: 
intFive = 5 :: Int 
-- a "floating-point" value of 10.3 
floatTenPointThree = 10.3 :: Float 

-- add them together with (+). This will not work... 
-- because both types are concretized (or specialized)
errorResult = intFive + floatTenPointThree 

-- add them together with (+). This will work
result = (fromIntegral intFive) + floatTenPointThree 
-- the result is 15.3
```

`fromIntegral` jest funkcją w języku Haskell, która konwertuje liczbę z jednego typu numerycznego na inny. Może być używana do konwertowania liczby z typu całkowitego na liczbę zmiennoprzecinkową lub odwrotnie. Przykład użycia:

`fromIntegral (length [1,2,3,4]) :: Float`

W tym przypadku funkcja `length` zwraca liczbę całkowitą, a `fromIntegral` konwertuje ją na liczbę zmiennoprzecinkową typu `Float`.



>[!important] `Num`
>So the `Num` typeclass means there actually isn’t only one definition for the functions for addition: `(+)`, subtraction: `(-)`, multiplication: `(*)`, negation: `negate`, etc but rather that each type — that is, each instance of `Num` — has **its own** definition for each of these functions.


# The Show Typeclass

There is a typeclass called `Show` and this provides a single function `show`







