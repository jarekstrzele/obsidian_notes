[[_ Haskell plac ćwiczeń dla uczonych]]

----
# Haskell i myślenie funkcyjne
>[!Najważniejsza idea programowania funcyjnego]
>Chodzi o **dane**!!!
>czyli
>jakie rodzaje danych w pewnej dziedzinie
>oraz
>jak chcemy je przekształcać

Dobry wprowadzeniem są *potoki* w powłokach uniksowych.

FizzBuzz
#fizzbuzz
```haskell
threes = cycle ["","", "Fizz"]
fives = cycle ["","", "", "", "Buzz"]
fizzbyzz = zipWith (++) threes fives
main = putStr (unlines fizzbuzz)
 ```

- definiujemy wyłącznie rodzaje danych, które są w domenie naszego problemu
oraz
- jakie przekształcenia chcemy na nich wykonać

---
## Typy danych są niedrogie

`data Bool = False | True`

Bool nie jest zdefiniowany w podstawowym Haskellu, ale bardzo łatwo go dodać

`data RGB = Red | Blue | Green deriving (Eq, Ord, Show, Enum)`
	- definiujemy trzy stałe Red, Blue, Green
	-  i automatycznie generujemy
		- testy na równość,
		- testy na uporządkowanie,
		- funkcję show oraz 
		- możliwość stosowania notacji `..` (np. `[Red..Green]` <=> `[Red, Blue, Green`)


**parametryczny typ polimorficzny**
`data Maybe a = Nothing | Just a`
reprezentuje pudełko, które jest albo puste (`Nothong`) albo zawiera jedną wartość jakiegoś typu   
zastosowanie: np. przekazywanie opcjonalne wartości lub zwracanie wartości, która jest nieobecna
>"Parametryczny polimorfizm oznacza, że można go używać dla dowolnie wybranej przez nas wartości (i) dowolnego typu"), więc nie jest ograniczony do, powiedzymy, łańcuchów"


polimorficzm parametryczny | polimorfizm OOP
--- | ---
używanie tego samego kodu do wszystkiego | pozwolenie na traktowanie różnych wartości w taki sam sposób

```haskell
data Person = Person { name :: String, age :: Maybe Int, fav_col :: RGB address :: [String]}

joe = Person "Joe" (Just 25) Red ["Durham Cathefral", "Durham"]

```
imię, opcjonalny wiek, ulubiony kolor, zero lub więcej wierszy adresu

### Funkcje pierwszoklasowe
te funkcje możemy traktować podobnie jak każdą inną częśc danych (budować je, przkazywać, używać)


----

## Dopasowywanie do wzorców



























