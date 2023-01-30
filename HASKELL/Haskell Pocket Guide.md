to run an app ->
`ghci` > `:l fileName.hs`
or
`runhaskell fileName.hs`

---
# INPUT OUTPUT
#haskell/input
#haskell/output

`getLine` get string from a user

```haskell
import System.IO

main :: IO()
main = do
    putStrLn "Type a word: "
    hFlush stdout
    lineFromUser <- getLine
    putStrLn $ "Word reversed: " ++ reverse lineFromUser
```

`hFlush stdout` 
- it has to be executed  before getting the word from the user
- the reason of that:
	- Haskell 


