[[_ 0 Complete Haskell Course]]
[[9 Solved Problems - HOFs]]

----
# HOF

>[!info] Higher Order Function (HOF)
>It is a function that receives or returns functions
>**key point**: Functions are first-class objects

## Predefined functions

### `map`
```haskell
map :: (a->b) -> [a] -> [b]
map f [] = []
map f (x:xs) = f x : map f xs

map odd [1..5]
[True, False, True, False, True]
```

### `(.)` returns  the composition of two functions
```haskell
(.) :: (b->c) -> (a->b)->(a->c)
(f . g) x = f (g x)

(reverse . sort) [5, 3, 5, 2]
[5,5, 3, 2]
```


## other
```haskell
apli2 :: (a->a)->a->a
apli2 f x = f (f x)

apli2' :: (a->a) -> (a->a)
apli2' f = f . f

---------
*Main> apli2 sqrt 16.0
2.0
*Main> :r
[1 of 1] Compiling Main             ( text.hs, interpreted )
Ok, one module loaded.
*Main> apli2' sqrt 16
2.0
*Main> 

```


----------
# Anonymous Functions ----(lambda `\`)

#lambda 

>[!info] Anonymous Functions (lambda functions)
>They are expressions that represent a function without name

```haskell
*Main> (\x -> x + 5) 3
8
--- add5 = \x -> 2 * x

*Main> map (\x -> x + 5) [1,2,3]
[6,7,8]

```


- they are usually used when they are short and only used once
- they are also usefull for performing program transformations


### important
##### Multiple parameters:
###### `\x y -> x + y` 
##### equals to
###### `\x -> \y -> x+y` 
##### which means
###### `\x -> (\y -> x+y)`


-------
# SECTIONS
#haskell/section

>[!info] Sections
>They allow partial infix operators to be applied

On the right | On the left
--- | ---
`(@ y) <=> \x -> x @ y` | `(y @) <=> \x -> y @ x`

```haskell
*Main> double = (* 2)
*Main> double 5
10

*Main> map (* 2) [1,2,3]
[2,4,6]

*Main> half = (/ 2) -- (2 /) this is different
*Main> half 6
3.0
*Main> half = (2 /)
*Main> half 6
0.3333333333333333

*Main> isUppercase = (`elem` ['A'..'Z'])
*Main> isUppercase 'c'
False
*Main> isUppercase 'A'
True

```


