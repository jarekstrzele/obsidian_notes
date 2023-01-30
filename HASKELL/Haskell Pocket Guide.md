to run an app ->
`ghci` > `:l fileName.hs`
or
`runhaskell fileName.hs`

---
# INPUT OUTPUT
#haskell/input
#haskell/output

`getLine` get string from a user

## input from a user
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
	- Haskell keeps words to print in a buffer
	- it will print words if in the buffer you pass a new word
	- `hFlush sdout` forces Haskellto print strings in the buffer
> `hFlush stdout` to funkcja, która natychmiast wypisuje wszystko, co jest w buforze wyjścia (stdout).


## Reading a file

read two first lines from the file:
```haskell
import System.IO

main :: IO()
main = do
    fileHandler <- openFile "myFile.txt" ReadMode
    size <- hFileSize fileHandler
    print size
    oneLine <- hGetLine fileHandler
    putStrLn oneLine
    oneLine <- hGetLine fileHandler
    putStrLn oneLine
    hClose fileHandler
```

read all line from the file
```haskell
import System.IO

main :: IO()
main = do
    fileHandler <- openFile "myFile.txt" ReadMode
    -- oneLine <- hGetLine fileHandler
    contents <- hGetContents fileHandler
    putStrLn contents
    hClose fileHandler
```

## Writing to a file



























