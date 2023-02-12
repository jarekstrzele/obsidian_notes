[[_ 0 Haskell for Imperative Programmers]]
#haskell/list 

https://www.youtube.com/watch?v=AN-P1-IvsKQ&list=PLe7Ei6viL6jGp1Rfu0dil1JH1SHk9bgDV&index=4

#haskell/list 

# Lists
- only one type 
- contructor `[]`, `x:[]`
	- `[1,2,3]`, `1:2:3:[]`

```haskell
generateListAsc :: Int->Int->[Int]
generateListAsc n m
  | m < n = []
  | m == n =[m]
  | m > n = n : generateListAsc (n+1) m

-- ghci> generateListAsc 10 3
-- []
-- ghci> generateListAsc 3 10
-- [3,4,5,6,7,8,9,10]
-- ghci> generateListAsc 3 3
-- [3]
```


## `import Data.List`

## some functions

`head`







