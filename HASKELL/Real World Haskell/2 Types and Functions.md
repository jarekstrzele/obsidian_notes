https://book.realworldhaskell.org/read/types-and-functions.html

**every expression and function in Haskell has a type**:
- `True :: Bool`
- `"Foo"::String`

>[!info] Type
>the type of a value indicates that it **shares** certain **properties** (concatenate lists, add numbers) with other values of the same type

 >[!info] abstraction
 >The benefit of introducing **abstraction** is that it lets us foget or ignore low-level details.
 >If I know that a value in my program is a sting, I don't have to know the intimate details of how string s are implemented.
 >**Haskell's type system allows us to think ar a very abstract level**
 
 
# Haskell's tpe system
## strong
- The type system guarantees that a program cannot contain cerain kinds of errors (int used like function -> Haskell's compiler generates an error)
- no automatic coercion/casting/conversion

**benefit** strong typing catches ewal bugs in our code before they can cayse problems


## static
The compiler knows the type of every value and expression at compile time, before any code is executed

## inferred
Finally, a Haskell compiler can automatically deduce the types of almost all expressions in a program. This process is known as _type inference_. Haskell allows us to explicitly declare the type of any value, but the presence of type inference means that this is almost always optional, not something we are required to do.


# Some common basic types



