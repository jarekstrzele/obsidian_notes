[[_ 0 Happy Learn Haskell]]

# Reusabiity
> **Functions are one of the most basic ways to re-use expressions in a program.**

Function take variables/parameters that can have different values (of a type) for each new time the function is applied.


# Functions are Values

Functions are a special kind of mapping-value from values to other values.

`putStgrLn` makes a kind of mapping between any `String` value to a corresponfing `IO()` value

e.g.
`plus5 x = x + 5`
`plus5` this is a function value (it is like socket); type `Int->Int`
`53` this is a Int value (it is like a plugin);type `Int`
`plus5 53` -> `58` this is a Int value (you connected the plugin to the socket); type `Int`




