#kotlin/hashcode

>[!info] `hashCode` 
>- to jest metodą, która jest dziedziczona z klasy `Any`, bazowej klasy dla wszystkich klas w Kotlinie,
>- metoda `hashCode` służy do generowania liczbowego kodu skrótu (*hash code*), który jest używany w różnych kontekstach, takich jak:
>> - implementacje kolekcji, 
>> - indeksowania obiektów,
>> - porównywanie obiektów.


Główne zasady związane z metodą `hashCode` to:

1. **Consistency with equals**: Jeśli dwa obiekty są równe według metody `equals()`, to ich `hashCode` powinien zwracać tę samą wartość. Z tego wynika, że obiekty różne pod względem `equals()` powinny mieć różne `hashCode`.
    
2. **Konsystencja w czasie życia obiektu**: Dla danego obiektu, `hashCode` powinien zawsze zwracać tę samą wartość podczas trwania życia tego obiektu, jeśli żadna zmienna wpływająca na wynik `hashCode` nie została zmieniona.

>[!danger] ważne
Jeśli mamy dwie referencje odwołujące się do tego samego obiektu, to wywołanie funkcji *hashCode* z użyciem każdej z tych referencji zwróci ten sam wynik.


# reguły przesłaniania funkcji `hashcode` i `equals`

1. Jeśli dwa obiekty są równe, muszą mieć te same kody mieszające.
2. Jeżeli dwa obiekty są równe, to wywołanie funkcji `equals` na rzecz każdego z nich musi zwracać `true` (`a.equals(b)`, `b.equals(a`).
3. Jeśli dwa obiekty mają taką samą wartość kodu mieszającego, to nie muszą być równe. Jeżeli jednak są równe, to muszą tę samą wartość kodu mieszającego.
4. a zatem jeśli przesłonisz funkcję `equals` . ,  musisz także przesłonić funkcję `hashCOde`.
5. Domyślne działanie funkcji `equals` polega na zwracaniu unikalnej liczby całkowitej dla każdego obiektu (czyli w klasach niebędących `data class` domyślnie dwa obiekty tego typu nigdy nie będą równe, chyba że zmienimy definicję funkcji `hascode`)
6. domyślnie `equals` porównuje wartości przy użyciou operatora ` === ` A zatem jeśli w klasie, która nie jest klasą danych, nie przesłonimy funkcji equals, to dwa obiekty nigdy nie zostaną uznane za równe, gdyż referencje do dwóch różnych obiektów zawsze będą zawierały inne kombinacje bitów.

#### `a.equals(b)` MUSI oznaczać, że `a.hashCOde() == b.hashCode()`

####
















