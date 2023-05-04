[[_ Real World Haskell]]

https://book.realworldhaskell.org/read/types-and-functions.html


**every expression and function in Haskell has a type**:
- `True :: Bool`
- `"Foo"::String`

>[!info] Type
>the type of a value indicates that it **shares** certain **properties** (concatenate lists, add numbers) with other values of the same type

 >[!info] abstraction
 >The benefit of introducing **abstraction** is that it lets us forget or ignore low-level details.
 >If I know that a value in my program is a string, I don't have to know the intimate details of how strings are implemented.
 >**Haskell's type system allows us to think at a very abstract level**
 
 
# Haskell's type system
## strong
- The type system guarantees that a program cannot contain cerain kinds of errors (int used like function -> Haskell's compiler generates an error)
- no automatic coercion/casting/conversion

**benefit** strong typing catches ewal bugs in our code before they can cayse problems


## static
The compiler knows the type of every value and expression at compile time, before any code is executed

## inferred
Finally, a Haskell compiler can automatically deduce the types of almost all expressions in a program. This process is known as _type inference_. Haskell allows us to explicitly declare the type of any value, but the presence of type inference means that this is almost always optional, not something we are required to do.


## lists, tuples
### list
`head [1,2,3]` -> `1`
`tail [1,2,3]` -> `[2,3]`
**list type** is ==polymorphic== because the values in a list can have any type


**Haskell tuples aren't immutable lists**







