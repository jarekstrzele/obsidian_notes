#ebook #helion #delphi #databases 


# Podstawowe operacje na bazach danych
Delphi obsługuje dwa typy lokalnych baz danych:
- Paradox
- dBase (*.dbf*)

ABy korzystać z baz danych potrzebujemy dwóch komponentów:
1. *TTable* (w zakładce BDE *Bortland DataBase Engine*) - definuje bazę daych
2. *TDataSource* (w zakładce *Data access*) - stanowi łącze między komponentem *TTable* a kontrolkami z zakładki *Data controls*

Komponenty z zakładki *Data Controls* (podobne do ich odpowiedników z zakładki Standard, Additional):
- TDBEdit
- TDBMemo
- TDBGrid
- TDBImage
- TDBChart
- TDBNavigator - pozwala na wykomnywanie różnyh ioperacji na rekordach baz danych
	- dodatkowe metody: `MoveBy(n)` przesunięcie rekordu bieżącego o `n` rekordów, `Append` dodanie  nowego rekordu na końcu baz danych (tabeli)

Korzystanie z kontrolek wymaga doinstalowania biliotek z `InstallSHield Express`

## Przeglądanie istniejących vaz danych w formacie `.dbf`
Dane można wyświetlać w:
- tabeli *TDBGrid*
- w okienkach *TDBEdit*
- w *TDBImage* przeglądanie pól .BMP
- *TDBMemo* przeglądanie pól typu tekstowego 


## zdanie 1
wyświetl w tabeli bazę Animals.dbf

rozwiązanie
- na formularzu umieść 
	- *TTable* (zakładka BDE) 
		- właściwość `DataBaseName` wymierz nazwę `DBDEMOS`
		- o
	- *TDataSource* (zakładka Data Access )
	- (zakładka Data Controls)
		- *TDBGrid*, *TDBNavigator*




