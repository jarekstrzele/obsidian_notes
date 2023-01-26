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

#haskell/typeclass
>[!important] Typeclass
>- it













