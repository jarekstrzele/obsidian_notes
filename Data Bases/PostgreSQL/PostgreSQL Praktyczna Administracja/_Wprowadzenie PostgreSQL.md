#udemy 
#PostgreSQL
#Łukasz_Bartnicki

---
# Wprowadzenie

https://dbadmin.net.pl/


## Architektura wielopoziomowa
Gdy startujesz instancje Postgresa to pojawia się 
==proces POSTMASTER== (jedna instancja jeden proces)

> PORT: 5432

Postmaster:
- powołuje obszary w pamięci `Shared Memory`
	- `Shared Buffers` przechowuje aktualnie przetwarzane dane
	- `WAL Buffers` zapisuje jako pierwszy zmiany wprowadzane przez użytkownika te zmiany `Wal writer ` zapisuje do `WAL Files`
- powołuje procesy backgroundowe
	- `BGWRITTER` pisze do plików zawartych w `Shared Buffers` (zapisuje po kawałku dane z shared buffera do pliku `DATA FILES`)
	- `CHECKPOINTER` zapisuje dane z shared buffera całe na raz do pliku oraz zapisuje DATĘ I CZAS zmian
	- `WAL Writer`
	- `ARCHIVER` [opcjonalny] zapisuje dane do `ARCHIVED WAL`
	- `LOG Writer`
	- `AUTOVACUUM` porządkowanie danych w obrębie plików (wydajność bazy danych optymalna)
	- `STATS COLLECTOR` statystyki bazy danych
- nasłuchuje aktywności użytkowników i wywołuje odpowiednie procesy (`5432`)


---

## Łączenie do bazy i pamięć `work_mem`
Gdy użytkowni łączy się z Postgresem, to łączy się z procesem `POSTMASTER`, który nasłuchuje na odpowiednim porcie `5432` lub innym.
DO obsługi zapytań użytkownika powoływany jest specjalny backgroundowy proces i powoływany jest obsar pamięci `work_mem`

> __work_mem__ w nim są wykonywana wszelkie operacje sortowanie i łączenia tabel

---

### Przetwarzanie zapytań
1. PARSOWANIE:
	1. sprawdzanie składni
	2. sprawdzanie typu zapytania
	3. rozłożenie zapytania na części pierwsze
2. OPTYMALIZACJA
	1. generowanie planu
	2. wybranie statystyk
	3. oblizanie kosztu
	4. wybranie planu
3. WYKONANIE zapytanie 


----

## Struktura plików

`PGDATA` to klaster, czyli katalog, w którym znajdują się dane postgresa; w tym folderze może być przechowywanych wiele baz


`PG_VERSION` plik testowy zawierający info wersji `cat PG_VERSION`


`base` wawiera dane wprowadzone przez użytkowanika?

`pg_tblspace` subdirectory containing symbolic links to tablespaces



























