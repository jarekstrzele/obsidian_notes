# _ Lern you a Haskell for Great Good

---
[[Installing]]
[[1 - Haskell Lists]]
[[1 - Haskell Tuples]]
[[2 - Types and Typeclasses]]
[[3 - Syntax in Function]]
[[4 Recursion]]




## Haskell
- pure functional programming language
- lazy
- statically typed - when you compile your program, the compiler knows which piece of code is a number, which is a string and so on

`ghci` interactive shell 
and `:l file_name` to load file `file_name.hs`
or `:r` to reload

---

Combin  simple fns  into more complex fns
```haskell
doubleMe x = x + x  
doubleUs x y = doubleMe x + doubleMe y
```

```ghci
doubleMe 9

```

```haskell
doubleSmallNumber x = if x > 100
			then x
			else x*2
```

`if` statement is an [[haskell expression | expression]]

```haskell
doubleSmallNumber` x = (if x > 100 then x else x*2) + 1
```


The function doesn't take any parameters, so it's a _definition_ or a _name_
```haskell
conanO'Brien = "It's a - me, Conan O'Brien!"
```









