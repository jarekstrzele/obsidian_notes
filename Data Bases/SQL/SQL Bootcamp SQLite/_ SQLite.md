[[_ SQL Bootcamp - SQLite cz. 1]]

[[_ SQL Bootcamp - SQLite cz. 2]]

---
[[DB Browser for SQLite or SQLitestudio | graficzne nakładki]]
[[_ Groupowanie danych SQLite]]
[[SELECT CASE SQLIte]]
[[Podzapytania SQLite]]
[[_ Łączenie tabel SQLite]]
[[Podsumowanie SQLite]]

---
# SQLite

## cechy
- serverless (bezserwerowa),
- zero konfiguracji
- międzyplatformowa
- samodzielna 
- transakcyjna (ATOM)
- lekka

www.sqlite.org

## architektura
- nie ma interakcji `client-server`
- zasobem współdzielonym przez aplikację jest plik bazy (schemat bazy danych +  dane znajdujące się w bazie) danych znajdujący się na twardym dysku
- obsługuje wielu użytkowników (ale nie jest to zbyt efektywne)
- jest możliwość zapytywania wielu baz danych

## zastosowania
- urządzenia wbudowane i internet rzeczy (IoT)
- aplikacje desktopowe
- app mobilne
- web development
- analiza danych
- data science
- pamięć podręczna (cache)
- ...
- 

## wady
- brak zarządzania użytkownikami (administracja na poziomie systemu plików)
- cała baza danych w jednym pliku
- nie można usunąć kolumny, dodać//usunąć ograniczeń tabeli (zawsze można utworzyć nową tabelę i usunąć starszą)
- widoki są tylko do odczytu
- jeden zapis zmian w jednym momencie

---
## Konfiguracja
https://sqlite.org/download.html

plik: windows: sqlite-tools-win.... (wypakować) (`sqlite.exe`) wiersz poleceń

`Connected to a transient in-memory database.` czyli gdy zamkniemy terminal zniknie baza
`.help` wszystkie dostępne komendy
`.tables` pokazuje wszystkie tabele
`.database` pokazuje BD do których mamy aktualnie dostęp

---
## tworzenie(łączenie się z) BD
`.open website.db` (stworzy plik w folderze, w którym uruchomiliśmy terminal, a jeżeli taka baza już jest, to ją otworzy)

---
## tworzenie tabeli
`sqlite> create table tech (id INTEGER, name TEXT);`

```sqlite
sqlite> insert into tech values (1, 'python');
sqlite> insert into tech values (2, 'java');

```

---
## zapisanie resultatu zapytania do pliku
```sqlite
sqlite> .once result.txt
sqlite> Select * from Category`
```
`.once nazwaPliku.rozszerzenie` tworzy nowy plik o danej nazwie

aby wysłać dane z nazwami kolumn:
`.header on`

#csv
aby wysłać dane do pliku CSV 
`.mode csv`



















