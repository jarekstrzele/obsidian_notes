*hello.hs*
```haskell
module Main where

main :: IO ()
main = do
    putStrLn "Hello, WOrld!"
```
- `module Main where` definiuje moduł o nazwie `Main`. Moduł to jednostka kompilacji w Haskellu.
- `main :: IO ()` definiuje funkcję `main`. Funkcja `main` jest funkcją punktu wejścia do programu.
- `main = do` definiuje blok kodu, który jest wykonywany przez funkcję `main`.
- `putStrLn "Hello, World!"` wyświetla napis "Hello, World!" na konsoli.

```powershell
> ghc .\hello.hs
> .\hello.exe
> Hello, WOrld!
```












