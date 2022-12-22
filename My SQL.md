# relacje
```sql
create table klasy(
	id_klasy int primary key auto_increment,
    nazwa varchar(100) not null
);
    
create table wychowawcy(
    id_wych int primary key auto_increment,
    imie text not null,
    nazwisko text not null,
    id_klasy int unique,
    foreign key (id_klasy) references klasy(id_klasy)
);
```



```sql
insert into klient( imie, nazwisko, email)
values ("Bikna", "Kiełbasa", "bky@aapp.pl") ;
select * from klient;

update klient set email="aaa@aaa.pl" where id_klienta between 2 and 3;
select min(id_klienta) from klient;

select * from user;
alter table klient change nazwisko Nazwisko text;

ALTER TABLE klient rename as User;

```













