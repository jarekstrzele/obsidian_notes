#haskell/maybe 

[[_ 0 Haskell for Imperative Programmers]]


# Basics
`f x`  returns:
- some result or
- error 

e.g the head of empty list? It is nothing

so:
`f x` in Haskell `Maybe`:
- `Just result`
- `Nothing`

```haskell
safediv :: Integral a => a -> a -> Maybe a
safedive a b = if b == 0 then Nothing else Just $ div a b
```

---
# `Data.Maybe`
```haskell
import Data.Maybe

isJust :: Maybe a -> Bool
isNothing :: Maybe a -> Bool 
fromJust :: Maybe a -> a

fromMaybe :: a -> Maybe a -> a

fromMaybe 3.1415 (Nothing) -- 

-- ...
```











