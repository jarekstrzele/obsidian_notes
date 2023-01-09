# Łączenie tabel
--- 1"26 łączenie tabel  
```sql
SELECT   
  klienci.idklient, imie, nazwisko,d ata_zamowienia, nazwa  
FROM klienci NATURAL JOIN zamowienia NATURAL JOIN produkty;  
  
SELECT   
  klienci.idklient, imie, nazwisko,d ata_zamowienia, nazwa  
FROM klienci LEFT JOIN zamowienia ON klienci.idklienta=zamowienia.idklienta  
                        LEFT JOIN produkty ON zamowienia.idproduktu = produkty.idproduktu

  

  

SELECT  
klienci.idklienta, imie nazwisko, data_zamowienia, nazwaFROM  
    klienci,   
    produkty,  
    zamowienia  
 WHERE  
   klienci.idklienta=zamowienia.idklienta and zamowienia.idproduktu = produkty.idproduktu 

  

```
  

---
# Relacje między tabelami
-- 1"03 Relacje między tabelami  

## wiele do wielu
co najmniej   trzy tabele  
klienci <-1---n--> zamówienia <--m---1--> produkty

_tab. zamówienia_:

-    jest tabelą łączącą produkty z klientami
-   zawiera id klienta (jeden klient może założyć wiele zamówień)
-   zwiera id produktu (w jednym zamówieniu może być wiele produktów)

mamy tabele _klienci, zamówienia_ (tę musimy zmodyfikować)  
dodajemy tabelę:  

>  create table produkty(  
>    idprodukty int auto-increment primary key,  
>    nazwa text not null  
> );

**modyfikujemy** _**zmówienia**  
_

>  _alter table zamowienia add column idproduktu int;_

> alter table zamowienia add foreign key (idproduktu) references produkty(idprodukty);

  

## jeden do wielu 
**klienci <---> zamówienia  (JEDEN klient może złożyć WIELE zamówień) w tab. zamówienia występuje kolumna zawierająca id klienta (pole nie musi być unikalne)  
  

>  create table klienci(  
>   idklienta int aut_increment primary key,  
>   imei text not null,  
> nazwisko text not null  
> );  
>   
> create table zamowienia(  
>   idzamowienia int auto_increment primary key,  
>   data_zamowienia date,  
>   **idklienta int,  
>   foreign key (idklienta)references klienci (idklienta)  
> )**

  

## jeden do jednego  
**klasa <--> wychowawca (jedna klasa ma jednego wychowawcę i na odwrót) (jeden rekord z tabeli klasy przypisany tylko do jednego rekordu z tabeli wychowawcy i na odwrót)  
klucz z tab. klasa jest też kluczem obcym w tabeli wychowawca (unique)  

> _create table klasy(  
> id_klasy int primary key auto_increment,  
> nazwa varchar(100) not null  
> )  
>   
> create table wychowawcy(  
> id_wychowawcy int primary key auto_increment,  
> imie text not null,  
> nazwisko text nor null,  
> **id_klasy int unique,**  
> **foreign key (id_klasy) references klasy(id_klasy)**  
> );_

  

---

# Modyfikacja tabel `ALTER TABLE`
-- 57"27 Modyfikacja tabel ALTER TABLE

ALTER TABLE user MODIFY pesel BIGINT  (zamiana kolumny _pesel_ w tabeli _user_ na _bigint_ 

ALTER TABLE user CHANGE aktywny czyAktywny bool ; (zamiana nazwy kolumny aktywny na czyAktywny

ALTER TABLE user RENAME as uzytkownik;  (zmiana nazwy tabeli user na użytkowniki)

  

  
---
# Zmiana i usuwanie danych w tablei
--- 52""55 ZMIANA I USUWANIE DANYCH W TABELI

_delete from user_  - usunie wszystkie wiersze

_delete from user  where id_user = 1_ - usuń  rekord o id `  
W Workbench jest zabezpieczenie przez przypadkową aktualizacją wszystkiego (Edit>Preferrencies>SQL Editor > na samym końcu  Safe Update:  

> > **update user set aktywny=1** -- wszystkie rekordy w tabeli user zmienią wartość kolumny aktywny na 1

_**poprawnie**_

_**update user set aktywny = 1 where id_user = 1 ;**  
_

  
---
# Grupowanie danych
--- 46"51 grupowanie danych  

**_select aktywny, count(*) from user group by aktywny having aktywny = 1 ;_** zgrupuj dane po kolumnie 'aktywny' i wyświetl tylko te dane, gdzie aktywny jest 1 (po group by nie można stosować where)

ale przed group by mogę użyć _where_  
_select aktywny, count(*) from user **where id_user > 1 group by aktywny having** aktywny = 1 ;_   

  

  

> select aktywny, count(*) from user group by aktywny;

* zlicza wszystkie pola, również _null_

select aktwny, count(aktywny) from user ;  <-- zliczy wszystkich ale bez null


---
# Dodawanie i pobieranie danych z tabeli
--- 28"10 Dodawanie i pobieranie danych z tabeli  

> insert into klient( imie, nazwisko, email)
> 
> values ("Zdziśo", "Śmietana", "zsy@aapp.pl") ;
> 
> select id_klienta as Num, imie as Imie, nazwisko as Naz 
> 
> from klient
> 
> where id_klienta > 1;

**Po _where_ nie ma przecinków**

SELECT imie as Imie, nazwisko as Nazwisko from user ;

INSERT INTO user  values( ... )

  

---13"55 Tworzenie tabel i baz danych

create table user (  
   id_user int auto_increment primary key,    imie text (50) not null,    nazwisko varchar(200) not null,    data_urodzenia date not null,    aktywny boolean,    plec enum('K', 'M'),    pesel int unique);

describe

  

_create database uzytkownicy default character set utf8 collate utf8_polish_ci ;_ utworzy bazę danych z obsługą polskich znaków  
drop database  uzytkownicy;   

use ;

select database(); -> jaką bazę używamy

show databases;  
show tables;

drop database uzytkownicy;

  

-----

pracujemy z Workbanch

services.msc - program z usługami w windowsi, szukamy mysql

instalacja MySQL (serwer, shell, ... porty domyślne 3306

DDL (Data Definition Language (operacje na tabelach: tworzenie, modyfikacja, usuwanie)  
DML(Data Manipulation Language (wybieranie, manipulowanie danymi)  
DCL (Data Control Language) (bezpieczeństwo dostępu do danyCH)