#haskell/types 
[[_ Real World Haskell]]

-------
[[#defining a new data type]]
[[#type synonyms]]
[[#algebraic data types]]
[[#Pattern matching]]
[[#Record syntax]]
[[#Parameterised types]]
[[#Recursive types]]
[[#Reporting errors]]
[[#Introducing local variable]]
[[#the offside rule and white space in an expression]]
[[#the case expression]]
[[#conditional evaluation with guards]]




--------------
# defining a new data type
### `data` keyword
```haskell
data BookInfo = Book Int String [String]
				deriving (Show)
				
```
- `BookInfo` it is our new type - this is **a type constructor** (a type name starts with a capital letter)
- `Book` it is **a value constructor** / data constructor; we use it to create a value of the `BookInfo` type (the value constructor star)



-------
# type synonyms




# algebraic data types




# Pattern matching








# Record syntax




# Parameterised types





# Recursive types






# Reporting errors













# Introducing  local variable












# the offside rule and white space in an expression













# the case expression





# conditional evaluation with guards
























