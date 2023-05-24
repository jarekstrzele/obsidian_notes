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
## definition
### `data` keyword
```haskell
data BookInfo = Book Int String [String]
				deriving (Show)
				
```
- `BookInfo` it is our new type - this is **a type constructor** (a type name starts with a capital letter)
- `Book` it is **a value constructor** / data constructor; we use it to create a value of the `BookInfo` type (the value constructor starts with a capital letter)
- `Int String [String]` are **components of the type** (similar to fields in  structures or classes) - components "` == ` " fields
	- `Int` - id
	- `String` - title
	- `[String]` names of its authors

## creation
```haskell
myInfo = Book 98342398 "Algebra of Programming" ["Richard Bird", "Oege de Moor"]
```






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
























