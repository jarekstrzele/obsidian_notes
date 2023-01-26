# Framework ADO.net
**ADO.NET** (ActiveX Data Objects for .NET) to interfejs programowania aplikacji (API) firmy Microsoft, który umożliwia aplikacjom:
- połączenie z bazami danych
- wykonywanie operacji na danych. 

**ADO.NET** jest częścią platformy .NET Framework i jest dostępny dla różnych języków programowania, takich jak C# i Visual Basic.

**ADO.NET** składa się z dwóch głównych części:
- `Data Provider` - warstwa połączenia z bazą danych, która umożliwia aplikacji:
	- wykonywanie zapytań
	- aktyalizowanie danych
- `DataSet`  to  warstwa pośrednicząca między aplikacją a bazą danych, która przechowuje dane w pamięci w postaci tabel i relacji, co pozwala na pracę z danymi niezależnie od źródła danych.

**ADO.NET** umożliwia dostęp do różnych typów baz danych, takich jak Microsoft SQL Server, Oracle, MySQL, itp. pozwala na tworzenie aplikacji korzystających z baz danych relacyjnych oraz pozwala na pracę z danymi w trybie offline.



---------------
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


*Visual Studio 2022* (2019) 
-> Nowy projekt
-> aplikacja konsoli .Net Framework
-> w projekcie musimy zainstalować KLIENTASQL
	-> Projekt>Zarządzanie pakietamy NuGet
		-> w wyszukiwarce: `Microsoft.Data.SqlClient` teraz jest `System.Data.SqlClient`

> obiekt `SqlConnectionStringBuilder`  jest używany do **określenia parametrów połączenia** z bazą danych, takich jak nazwa hosta, nazwa bazy danych i metoda uwierzytelniania.

> Obiekt `SqlConnection` jest klasą w bibliotece ADO.NET, która jest używana **do połączenia z bazą danych SQL Server.** Klasa ta pozwala na otwarcie i zamknięcie połączenia, a także na konfigurację parametrów połączenia, takich jak nazwa hosta, nazwa bazy danych, nazwa użytkownika i hasło.

> **Słowo kluczowe "using"** jest używane w C# do automatycznego zarządzania zasobami. W przypadku użycia "using" przed definicją obiektu, po zakończeniu działania kodu w bloku using, obiekt jest automatycznie zamykany i jego zasoby są zwolnione.
> Głównym celem tego mechanizmu jest **uniknięcie problemów związanych z brakiem zwolnienia zasobów przez programistę**, co może prowadzić do problemów z wydajnością i stabilnością aplikacji.

> Obiekt `SqlCommand` jest klasą w bibliotece ADO.NET, która jest używana do **wykonywania zapytań** SQL na bazie danych SQL Server. Klasa ta pozwala na utworzenie i wykonanie zapytania, a także na konfigurację parametrów zapytania, takich jak tekst zapytania i połączenie z bazą danych.
> Obiekt SqlCommand jest tworzony za pomocą konstruktora, który przyjmuje dwa argumenty: 
> 	- tekst zapytania oraz 
> 	- obiekt połączenia z bazą danych. 
> Następnie, zapytanie jest wykonywane przy użyciu metody 
> 	- `ExecuteReader()`,
> 	- `ExecuteNonQuery()` lub
> 	- `ExecuteScalar()`, 
> w zależności od typu zapytania.

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Data.SqlClient;

namespace ConnectionExampleCorret
{
    internal class Program
    {
        static void Main(string[] args)
        {
            try
            {
   SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder();
   builder.DataSource = "DESKTOP-2AAK5H9\\SQLEXPRESS_FIRST";
    builder.InitialCatalog = "ShopDB";
    builder.IntegratedSecurity= true;
    using (SqlConnection connection = new SqlConnection(builder.ConnectionString))
                {
    Console.WriteLine("Imiona z tabeli Cusomers");
    Console.WriteLine("==========================");
    String sql = "SELECT FirstName from Customers";
    using (SqlCommand command = new SqlCommand(sql, connection))
    {
     connection.Open();
     using (SqlDataReader reader = command.ExecuteReader())
     {
      while (reader.Read())
	      Console.WriteLine(reader.GetString(0));
                            }
                        }
                    }
                }
            }
catch(SqlException e)
  {
   Console.WriteLine(e.ToString());
   }
   Console.WriteLine();
   }
 }
}

```

'18:00


----------------














