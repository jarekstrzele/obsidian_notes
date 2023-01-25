**Bazy danych**:
- Oracle (elastyczna, nieprzyjazna)
- Microsoft (nieelastyczna, przyjazna)
**Wersje SQL Server** :  
- Express Edition (free)  
  - custom, na dysku D, New SQL Server
- Standard, Enterprise  
  
**Potrzebna oprogramowanie**:  
- Visual Studio 2019 Express  
- SQL Sever 2019 Express oraz Mangement Studio


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
```sql
select Count(FirstName) from Customers;
select Count(FirstName), SecondName from Customer;
select top 3 FirstName, SecondName from Customers;
select top 20 percent FirstName, SecondName from Customers;

select top 3 * from Customers;
select top 20 percent * from Customers;

select top 4  FirstName as [First Name], ContactName as [Constact Name] from Customers

select distinct FirstName  from Customers;

ALTER TABLE Customers
ALTER COLUMN Phone   VARCHAR(100);


select Address + ' ' + City + ' ' + Country as TwojAdres from Customers;

```


---
# Wyświetlanie danych - operatory prównania i logiczne

`>,    <,    =,    >=,     <=,  <>`


```sql
 select * from Customers where idCutomer >3;

 select idCutomer, FirstName as [Imię], SecondName as [Nazwisko] from Customers where idCutomer =3;

 select idCutomer, FirstName as [Imię], SecondName as [Nazwisko] from Customers where idCutomer <> 3;

select * from Customers where City <> 'Warszawa';

select * from Customers where City > 'Warszawa';


```

`all()`, `any()`

```sql
select * from Customers where idCutomer between 2 and 3;

select * from Customers where City in('Gdańsk', 'Wrocław');

```

`like 'r%'' zaczyna się od r
`not like 'r%'' nie zaczyna się od r

--------
# .NET









