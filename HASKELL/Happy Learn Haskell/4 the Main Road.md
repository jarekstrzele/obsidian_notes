[[_ 0 Happy Learn Haskell]]

#haskell/main
`main` 
- is a entry-point of all Haskell programs
- is an action

[[3 Types as Jigsaw Pieces#definition]]
>[!info] Haskell programs
>They are **made** by writing definitions in text files.
>They are **running** by calling a compiler on thsoe text files.
>The **compiler**:
>		- understands Haskell
>		- translates the text files as Haskell into an executable program
>		- that program can be run

## pure
#haskell/pure
**are**:
- definitions
- values (values that produce actions)
- expressions
- functions

**means** they are:
- consistent
- equational
- express truths about values

**pure** 1 + 5 = 6 (it's always. it's never get a different result; true/false absolutly)
**real** the current time is NOT pure value because it is ALWAYS changing

