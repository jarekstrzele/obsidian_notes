> [!info] baza danych
> to zestaw obiektów, na których można wykonać CRUD
> te obiekty to tabele, widoki, indeksy, funkcje ...

> [!info] tabela
> obiekt, w którym przechowywane są dane
> każda baza danych musi mieć zdefiniowaną przynajmniej jedną tabelę

**kolumna** - zbiór komórek w porządku pionowo
**wiersz** - zbiór komórek w porządku poziomym
**programy** procedury składowane (np. zmiana nazwy kolumny bez utraty danych w kolumnie)
**indeks** obiekt podobny do indeksów na końcu podręczników (przyspieszają wyszukiwanie w bazie danych)
**widok** to takie wirtualne tabele
**funkcja** obiekt podobny do procedury składowanej, ale przetwarza bądź zwraca JEDEN WIERSZ danych

---
# Rodzaje baz danych
# OLTP
- fundament bazy, cały czas dochodzi do różnych zmian
- baza w tym systemie musi działać bardzo szybko


# OLAP
- zmiany w systemie będa robione bardzo żadko 
- system będący podstawą do zadań analitycznych


----
# Normalizacja baz danych

## pierwsza postać normalna
tabele muszą być pogrupowane w taki sposób, że
- dane w kolumnach są atomowe
- jest klucz główny

## druga postać normalna
dana tabela dotyczy jednej klasy obiektu
(błąd: np. jedna tabela z danymi o klientach i produktach)


## trzecia postać normalna
tu trzeba wiedzieć, czym jest klucz główny
**klucz główny** to zbiór kolumn, które nie mogą się powtarzać 
w tabeli są kolumny, które zależą od klucza głównego, ale nie zależą od pozostałych kolumn

(30"00)

---
# Pobieranie danych z bazy









