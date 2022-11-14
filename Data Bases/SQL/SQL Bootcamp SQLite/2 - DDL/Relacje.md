[[_ DDL SQLite]]


----
# Relacje
>*Entity Relationship* (modelowanie związków) - przedstawienie wpostaci diagrmu ERD (*Entity Telationship Diagram*) związków między danymi w bazie danych

najpierw diagram -> potem język SQL

> **ENCJA** (jakby klasa OOP; tabela) zbiór obiektów o tych samych cechach, w diagramach ERD encja przedstawiana  jest anjczęściej jako prostokąt

>**ZWIĄZEK** zbiór istototnych powiązań między encjami, w diagramach ERD reprezentacją związku jest linia łącząca encje (prostokąty)


---
## One-to-One
z każdym elementem jednej tabeli jest powiązany tylko jeden element z drugiej tabeli i na odwrót

gdy w jednej tabeli, klucz  główny jest jednocześnie głównym i obcym w drugiej tabeli (`user.id(PK` <-> `developer.user_id(PK, FK1)`)

```sql
CREATE TABLE user(
    id INTEGER PRIMARY KEY,
    first_name TEXT NOT NULL,
    last_name  TEXT NOT NULL,
    gender TEXT,
    birth_date TEXT
);

CREATE TABLE developer(
    user_id INTEGER PRIMARY KEY REFERENCES user(id),
    job_title TEXT NOT NULL, 
    department TEXT NOT NULL
);

```


---
## One-to-Many
najbardzie powszechny typ relacji
dla wiersza z tabeli pierwszej może istnieć wiele zgodnych wierszy z tabeli drugiej, ale nie na odwrót

np.
- jeden departament może mieć wielu pracowników
- jeden pracownik tylko w jednym departamencie (klucz obcy znajduje się po stronie wielu, czyli w tabeli pracownicy)

```sql
DROP TABLE IF EXISTS department;
DROP TABLE IF EXISTS employee;


CREATE TABLE department(
    id INTEGER PRIMARY KEY,
    dept_name TEXT NOT NULL,
    dept_code TEXT NOT NULL
    );
    
CREATE TABLE employee(
    id INTEGER PRIMARY KEY,
    first_name TEXT NOT NULL,
    last_name TEXT NOT NULL,
    hire_date TEXT NOT NULL,
    department_id INTEGER NOT NULL REFERENCES department(id)
    );
    
INSERT INTO department(dept_name, dept_code)
VALUES ('Information Technology', 'IT'),
        ('Sales', 'SLS')
        ,('HumanResources', 'HR');
        

INSERT INTO employee(first_name, last_name, hire_date, department_id)
VALUES ('Tom', 'Cooper', '2020-01-10', 1),
        ('John', 'Smith', '2015-02-10', 3),
        ('Mike', 'Pond', '2013-04-10', 2),
        ('Alice', 'Cooper', '2016-01-22', 3);
        
select * from department;

select e.first_name, e.last_name, d.dept_name
from employee as e
join department as d 
    on e.department_id = d.id;


first_name	 last_name	dept_name
Tom	         Cooper	    Information Technology
John	     Smith	    HumanResources
Mike	     Pond       Sales
Alice	     Cooper	    HumanResources
```


---
## Many-to-Many
- często stosowana jest  tabela pośrednia łącząca dwie pierwsze podstawowe (**tabela krzyżowań**. **most**)
- wielu użytkowników Facebooka może należeć do wielu grup oraz wiele grup może mieć wielu użytkowników

### bridge
- ta relacja to w sumie dwie relacje **one-to-many**
- **bridge** dla nie to np.
	- kolumna `id` z tabeli `user` **`user_id(PK, FK1)`**
	- kolumna `id` z tabeli `fb_group` **`fb_group_id(PK, FK2)`**
	- te dwie kolumny razem będą kluczem głównym a `FK1` to id usera oraz `FK2` to id grupy 
	- można do tej dodatkowej tabeli dodawać inne kolumny z oczekiwanymi informacjami np.: data przyłączenia do grupy
NAJPIERW USUWAMY `bridge` potem połączone kolumny
```sql
DROP TABLE IF EXISTS user_fb;
DROP TABLE IF EXISTS fb_group;

CREATE TABLE user_fb (
    id INTEGER PRIMARY KEY,
    nick TEXT NOT NULL
    );
    
CREATE TABLE fb_group(
    id INTEGER PRIMARY KEY,
    group_name TEXT NOT NULL
);

INSERT INTO user_fb(nick)
VALUES ('karo234'), ('zelu232'), ('cv_geek'),('zmont_862'),('machu21'),('nocan');
        
INSERT INTO fb_group(group_name)
VALUES ('Python'), ('Bog Data'), ('Inwestowanie'), ('Oferty pracy IT'), ('Football');

select * FROM user_fb;
select * from fb_group;

CREATE TABLE bridge(
    user_id INTEGER REFERENCES user_fb (id),
    fb_group INTEGER REFERENCES fb_group (id),
    PRIMARY KEY (user_id, fb_group)
);
INSERT INTO bridge(user_id, fb_group)
VALUES (1,2), (1,4), (2,1), (2,2), (2,3), (4,1),(4,2), (6,2), (6,3);

-- do jakich grup należy użytkownik id=2
-- result: 1-Python,2-Bog Data,3-Inwestowania
select user_fb.nick, fb_group.group_name
from user_fb
join bridge on user_fb.id = bridge.user_id
join fb_group on bridge.fb_group = fb_group.id
where user_fb.id = 2;

```






---







