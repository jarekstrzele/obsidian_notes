[[0 - Haskell intro]]



---
# Tuples
- They are like lists (store several values into a single value)
- Its type depends on how many components it has and the types  of the components
- they can contain a combination of several types
- there is no such thing as a singleton tuple
`(1,2)  ("One", 2)   ("Chris", "Dow", 32)`

## function 
`fst` takes a pair and returns its first component`
`snd` takes a pair an returns its second component
```haskell
ghci> fst (10,20)
10
ghci> snd (10,20)
20

```

`zip` produce a list of pairs; it takes two lists and then sips them together  into one list by joining the matchin elements into pairs
```haskell
ghci> zip [1,2,3,4,5] [5,5,5,5,5]
[(1,5),(2,5),(3,5),(4,5),(5,5)]
ghci> 

ghci> zip [1 .. 5] ["one", "two", "three", "four", "five"]  
[(1,"one"),(2,"two"),(3,"three"),(4,"four"),(5,"five")]
ghci> zip [1 .. 15] ["one", "two", "three", "four", "five"]  
[(1,"one"),(2,"two"),(3,"three"),(4,"four"),(5,"five")]
ghci> 

```


```haskell
ghci> let triangles = [(a,b,c) | c <- [1..10], b<-[1..c], a<-[1..b], a^2 + b^2== c^2]
ghci> triangles 
[(3,4,5),(6,8,10)]
```
