
```haskell
ghci> import Data.List
ghci> isInfixOf "Haskell" "abeowif haskell fwefji"
False
ghci> isInfixOf "Haskell" "abeowif Haskell fwefji"
True
ghci> isInfixOf "Haskell" "abeowifHaskellfwefji"
True
ghci> let someList = ["to", "ku", "zali", "piko"]
ghci> someList !! 0
"to"
ghci> someList !! 1
"ku"
ghci> 

```