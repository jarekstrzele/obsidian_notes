
praca na Ubuntu

------
# Instalacja
1. GHC (Glasgow Haskell Compiler)
2. Cabal (narzędzie do zarządzania pakietami)


```bash
sudo apt install ghc cabal-install

# sprawdzenie instalacji
ghc --version
cabal --version

```

`HelloWorld.hs`
```haskell
main :: IO ()
main = putStrLn "Hello, Haskell"
```


> 
wyjaśnienie:
- Każdy program w Haskellu potrzebuje funkcji `main`, która służy jako punkt wejścia programu. Funkcja ta jest specjalna, ponieważ jest wywoływana, kiedy uruchamiasz skompilowany program.
- `main :: IO ()`
	- `main` - to nazwa funkcji
	- `::` - oznacza deklarację typu funkcji
	- `IO ()` typ zwracany przez funkcję `main`:
		- `IO` oznacza, że funkcja wykonuje operacje wejścia/wyjścia
		- `()` typ jednostkowy, czyli nie zwraca żadnej wartości
- `main = putStrLn "Hello, Haskell`
	- ` = ` służy do definiowania wartości funkcji









# uruchamianie
## kompilowanie
```bash
ghc HelloWorld.hs -o hello

./hello

```

## bez kompilacji
```
runghc nazwapliku.hs
```

> [!important] wyjaśnienie
> Instrukcja `runghc` jest narzędziem dostarczonym wraz z Glasgow Haskell Compiler (GHC), które pozwala na uruchomienie skryptów napisanych w Haskellu bez konieczności ich wcześniejszej kompilacji do pliku wykonywalnego. Jest to wygodne narzędzie dla programistów, którzy chcą szybko testować i uruchamiać swoje programy w Haskellu.






