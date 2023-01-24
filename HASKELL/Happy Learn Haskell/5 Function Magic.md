[[_ 0 Happy Learn Haskell]]
`True :: Bool` - True has a Bool type
`False :: Bool`

**lambda function**/ **function literal** `\x-> True` (explanation: an inline function definition)

**function** :
- it is a way of getting a completely new value from an existing value (from existing or no-existing value)
- function like othe values can be passed into other function or return from functions

`\x->x`, `\x->True`
`(\x -> True) False` -- equals True
`(\x->True)((\x->True) False)` -- equals True

```haskell
lambdaCoin :: Bool -> Bool
lambdaCoin = \x -> True
```

```haskell
-- the function that always returns True no matter what Bool it gets lambdaCoin :: Bool -> Bool lambdaCoin = \_ -> True -- the value True, by applying the above lambdaCoin -- function to the value False newCoin :: Bool newCoin = lambdaCoin False -- the value True, by applying the above lambdaCoin -- function to newCoin which is itself arrived at by -- applying lambdaCoin to False newCoinAgain :: Bool newCoinAgain = lambdaCoin newCoin -- this is another way to write newCoinAgain, -- but explicitly spelling out -- all of the applications of lambdaCoin newCoinAgain' :: Bool newCoinAgain' = lambdaCoin (lambdaCoin False)
```





