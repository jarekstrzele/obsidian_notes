#youtube #postgresql/function 
https://www.youtube.com/watch?v=3K32mdb6h5E
https://docplayer.pl/55003112-W-postgresql-mamy-do-dyspozycji-nie-tylko-funkcje-wbudowane-ale-rowniez-mozemy-tworzyc-wlasne-sa-one-zapisywane-w-tabeli-systemowej-pg_proc.html


```sql
create [or replace] function func_name(parms)
	return return_type
	language plpgsql
	as
$$
declare
-- variable declaration
begin
	--logic
end ;
$$
```

to call
`select func_name(args) ;`

Funkcje są zapisywane w  w tabeli systemowej **pg_proc**
Tworzenie własnych funkcji
```sql
CREATE [OR REPLACE] FUNCTION nazwa_funkcji([typ_funkcji])
	RETURNS typ_wyniku_funkcji
	AS definicja_funkcji
	LANGUAGE 'nazwa hęzyka';
```

`SELECT * FROM pg_language;` list języków

### named notation
```
select func_name(
	len_from => 40,
	len_to => 90
) ;
```

### mixed notation
*position notation first*
```
select func_name(
	40,
	len_to => 90 
) ;
```

example
```sql
CREATE TABLE book( 
	isbn INT NOT NULL,
	title VARCHAR(30),
	total_copies int,
	price float4
) ;

INSERT INTO book (isbn, title, total_copies, price)
VALUES (1006, 'Pan Włodyjoski', 11, 234.21);

```

defining a function
```sql

create or replace function book_copies(min_copies int)
returns INT 
as 
$$
declare 
	copies int;
begin 
	select count(*) into copies from book where total_copies > min_copies;
	return copies ;
end ;
 
$$ language plpgsql

```

to use
`select book_copies(5)`


przykład
funkcja dodająca 1 do podajnej liczby (PL/pgSQL)
```PL/pgSQL
CREATE FUNCTION dodaj_jeden(int4) RETURNS  int4 AS '
	BEGIN
		RETURN $1+1 ;
	END ;
'language 'plpgsql';
```
aby wyświetlić jej działanie:
`SELECT dodaj_jeden(3) AS wynik ;`

aby skasować
`DROP FUNCTIOn dpdak_jeden(int4);`

## JĘZYK SQL
aby zwrócić więcej niż jeden wiersz `setof`
```sql
CREATE FUNCTION klienci(text) RETURNS setof customer AS'

SELECT * FROM customer WHERE town=$1;

'LANGUAGE 'SQL';
```


## Język PL/pgSQL
#pl/pgsql

To język blokowo-strukturalny
```sql
[etykiera]
[DECLARE deklaracje]
BEGIN
	instrukcje ;
	[RETURN wyrażenie_zwracane] ;
END;

```


- **etykieta** , **deklaracje** są opcjonalne dla każdego zbloków
- blokowy zakres zmiennych (nazwy zmiennych w bloky wewnętrznym przesłaniają takie same nazwy z bloku zewnętrznego)

### funkcja bez argumentów
```pl/pgsql
CREATE or REPLACE FUNCTION ex01()
RETURNS text
LANGUAGE plpgsql AS $$
	begin
		RETURN 'hello word'  ;
	end ;	
$$;

select ex01();
```


### funkcja z argumentami
```pl/pgsql

CREATE OR REPLACE FUNCTION ex03(real)
RETURNS real
LANGUAGE plpgsql AS
$$
BEGIN
 RETURN $1*$1;
END ;
 
$$;


CREATE OR REPLACE FUNCTION ex03(real, int)
RETURNS real
LANGUAGE plpgsql AS
$$
BEGIN
 RETURN $1*$2;
END ;
 
$$;

select ex03(10,21);






create function zmienne1(int4) RETURNS float8 AS 
$$
DECLARE
	n integer := 1;
	my_pi CONSTANT float8 = pi();
	r ALIAS FOR $1 ;
BEGIN
 	return my_pi * r * r;
END;
$$ language 'plpgsql';
```


### aliasy parametrów wejściowych
```
CREATE OR REPLACE FUNCTION ex04(real)
RETURNS real
$$
DECLARE
param ALIAS FOR $1;

BEGIN
	RETURN param*param ;
END;
$$
```



### typ zmiennej określny przez atrybut tabeli
#### `zmienna tabela.atrybut%TYPE`

```sql
CREATE TABLE ex05t(
	id serial,
	name varchar(10),
	hiredate date
);
```

```sql
CREATE OR REPLACE FUNCTION ex05(ex05t.name%TYPE, ex05t.hiredate%TYPE)
RETURNS text
LANGUAGE plpgsql AS 
$$
BEGIN
 	return $1||' '|| $2 ;
end;

$$ ;


select ex05('Julia', '1009-01-01');
```


### type wierszowy

##### `nazwa tabela%ROWTYPE ;` -> wynikiem tej deklaracji jest zmienna zwierająca pola, po jednym dla każdej kolumny tabeli, na podstawie której powstała.

aby skorzystać z pól: `zmienna.pole`

`RECORD` ten typ jest wypełniany wartościami w czsie wykonani
```sql
CREATE TABLE ex06t(id serial, name varchar(10), hiredate date ) ;

INSERT INTO ex06t VALUES (DEFAULT, 'KOWALSKI', '2007-01-01') ;
INSERT INTO ex06t VALUES (DEFAULT, 'NOWAK', '2017-05-09') ;

CREATE OR REPLACE FUNCTION ex06(ex06t)
RETURNS text LANGUAGE plpgsql AS
$$
DECLARE
	x ex06t;
BEGIN
	x.name := $1.name;
	x.hiredate := $1.hiredate;
	return x.name || '  zatrudniony od  ' || x.hiredate ;
END

$$;

select ex06(taka.*) from ex06t taka;
```


## Kwerenda, która nie zwraca rezultatu
```sql
CREATE table ex07t(id serial, name varchar(10), hiredate date) ;

create or replace function ex07 (varchar, date)
returns void 
language plpgsql as
$$
 Begin 
 	insert into ex07t VALUES(default, $1, $2) ;
	return ; 
	end ;
  
$$ ;

select ex07('Alibaba', '2123-07-02') ;
select * from ex07t ;
```

### Kwerenda zwracające jeden wiersz

```sql
INSERT INTO ex08t VALUES(Default, 'Anonim', '2222-02-02') ;


create or replace function ex08 (varchar)
returns text 
language plpgsql as
$$
declare
val record ;
 Begin 
 	select * into val from ex08t where name=$1 ;
	RETURN val.name || ' zatrudnionu ' || val.hiredate ;
	end ;
  
$$ ;

select ex08('Anonim') ;
```

### instrukcje warunkowe

```sql
create table ex10t (id serial, name varchar(10), sal numeric) ;

CREATE or REPLACE FUNCTION ex10(varchar, numeric)
returns integer 
language plpgsql as
$$
DECLARE
	err integer;
BEGIN
	if $2>=0 THEN
		insert into ex10t values (default, $1, $2) ;
	end if ;
	get diagnostics err := row_count;
	return err ;
end ;
$$ ;

select ex10('kowalski', 1200); --zwraca 1
select ex10('kiklok', -500) ; -- zwraca 0
select * from ex10t; -- tylko jeden rekord
```

## Pętle
```sql
create or replace function ex11(integer, integer)
returns setof integer 
language plpgsql AS
$$
begin
	for i in $1 .. $2 LOOP
		return next  2^i ;
	end LOOP ;
	return ;
end
$$;

select * from ex11(3,10) ;
```










