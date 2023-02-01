[[0 - Haskell intro]]

>[!info] HOF
> A function that take functions as parameters or return functions as return values.


# Curried functions
==Every functions in Haskell officially only takes one parameter!!==

If a function accepts several parameters is **curried function**
```haskell
ghci> max 4 5
5
ghci> (max 4) 5
5
```

Putting a space between two things is simply **function application!!!**.
The space is sort of like an operator and it has the highest precedence.
`max::(Ord a)=> a->a->a` that can also be written:
`max:(ord a)=>a->(a->a)` - `max` takes an `a` and returns a function that takes an `a` and returns an `a`







