[[_0 Learn FastAPI by building a complate project]]


# Working with DBs
#databases 

## Relational DB
tables, fields, relations, static schema

## Non-relational databases
No-SQL
#node sql
### Types of NoSQL dbs:
#### Document-oriented databases
a document store
It is desugned for:
- storing
- retrieving
- managing
document-oriented information
pair: each key with a complex data structure (called a document)

#### Key_value Stores
Each key is associated with only one value in a collection (like a dictionary)
the most simplest db

#### Wide-Column Stores
It uses tables, rows, columns but names and formats of the cols can vary from row to row in the same table

#### Graph Stores
a graph db uses graph structures for semantic queries with nodes, edgrs, and properties to represent and store data

## SQL
Structure Query Language


## ORM Object-Relational-Mapper
#python/orm 
Object-relational-mapping is the idea of being able to write queries, using the OOP of your preferred programing language - interact with our db using our language f choice instead of SQL
`customer.select()`

**Why**
- abstracts away teh database system so that switching from MySQL to Postrgres is easy
- Depending on the ORM you get a lot of advanced features out of the box, such as support for transactions, connection pooling, migrations, seeds, streams
- many of the queries you write will perform better if you are not SQL master


### MODELS
#python/orm_model
> [!model]
> It is a single, definitive source of information about your data. It contains the essential fields and behaviors of the data your're storing. Generally each model maps to a single database table
> a MODEL --> a TABLE

```python
customers =sqlachemy.Table(
	"cutomers",
	metadata,
	sqlalchemy.Column("id", sqlachemy.Integer, primary_key=True),
	sqlalchemy.Column("customer"m sqlalchemy.String),
	sqlalchemy.Column("address", sqlalchemy.String),
)
```


### CRUD
Create -- 
Read -- retrieve
Update -- modify
Delete -- destroy

## POSTGRES
[[PostgreSQL ogólne]]

### to install on linux
ubuntu 20.04
https://www.digitalocean.com/community/tutorials/how-to-install-postgresql-on-ubuntu-20-04-quickstart
ubuntu 22.04
https://www.digitalocean.com/community/tutorials/how-to-install-postgresql-on-ubuntu-22-04-quickstart
user: postgres
password:  ---

`sudo -u postgres psql` to enter the postgres sever in the terminal

### PGAdmin4
[[Data Bases/PostgreSQL/PostgreSQL ogólne | Instalacja na Linuksie]]

26.08.2022
js100code@gmail.com
Filozofia2!@
 http://127.0.0.1/pgadmin4
użytkownik:postgres
Filozofia2

```shell
$ su postgres
Password: 
postgres@jarek-Lenovo-G700:/home/jarek/MEGAsync/0PROG/docker/firstDockerApp/NodeExpressMongoDBDockerApp$ psql -c "ALTER USER postgres PASSWORD 'root';"
could not change directory to "/home/jarek/MEGAsync/0PROG/docker/firstDockerApp/NodeExpressMongoDBDockerApp": Permission denied
ALTER ROLE

```

Add new server 
Add a new db  "store"
PyCharm, new project
`pip install sqlalchemy`
`pip install databases asyncpg psycopg2 psycopg2-binary`

some problems with `psycopg2`
https://www.psycopg.org/docs/install.html

### First app
```python
import databases
import sqlalchemy

DATABASE_URL="postgresql://postgres:root@localhost:5432/store"

# `root` is a passwd for the postgres user


database = databases.Database(DATABASE_URL)
metadata = sqlalchemy.MetaData()

books = sqlalchemy.Table(
    "books",
    metadata,
    sqlalchemy.Column("id", sqlalchemy.Integer, primary_key=True),
    sqlalchemy.Column("title", sqlalchemy.String),
    sqlalchemy.Column("author", sqlalchemy.Integer),

)
```


```python
async def shutdown():
    await database.disconnect()


@app.get("/books/")
async def get_all_books():
    query = books.select()

    # this method fetches all existing queries,
    # all existing records from this query in our case logs select
    # and then it's going to return a list
    return await database.fetch_all(query)

@app.post("/books/")
async def create_book(request: Request):
    data = await request.json()
    query = books.insert().values(**data)
    last_record_id = await database.execute(query)
    return {"id": last_record_id}
```

## Postman
New collection (Demo Fast, Fastapi store) (three dots and *add request* -> `get all books` )



## Alembic
#python/alembic
>[!alembic]
>It is a migration manager
>It is like a system version control

You can "travel" (like on Git) through the history of you app.

`pip install alembic`

`alembic init migrations` this will create migrations:
- it creates a subfolder `mgrations`
	- configiure a file `env.py`:
		- `from main import metadata`
		- `target_metdata = metadata`
- it creates a file `alembic ini`:
	- in this folder you have to configurate: `sqlalchemy.url = postgresql://postgres:root@localhost:5432/store`

We deleted a table.

`alembic revision --autogenerate -m "Initial"` 
```shell
1$ alembic upgrade head
INFO  [alembic.runtime.migration] Context impl PostgresqlImpl.
INFO  [alembic.runtime.migration] Will assume transactional DDL.
INFO  [alembic.runtime.migration] Running upgrade  -> 236e355d1b3e, Inistial
```
the  book table rebuilded

## Create one-to-many
a reader can have multiple books

You made same changes in your object-oriented tables
```python
books = sqlalchemy.Table(
    "books",
    metadata,
    sqlalchemy.Column("id", sqlalchemy.Integer, primary_key=True),
    sqlalchemy.Column("title", sqlalchemy.String),
    sqlalchemy.Column("author", sqlalchemy.String),
    sqlalchemy.Column("pages", sqlalchemy.String),
    sqlalchemy.Column("reader_id", sqlalchemy.ForeignKey("readers.id"), nullable=False, index=True),
)
# .ForeignKey("table_name")
# index=True because we may want to search in books table for reader_ID

readers = sqlalchemy.Table(
    "readers",
    metadata,
    sqlalchemy.Column("id", sqlalchemy.Integer, primary_key=True),
    sqlalchemy.Column("first_name", sqlalchemy.String),
    sqlalchemy.Column("last_name", sqlalchemy.String),
)

```
, so:
`alembic revision --autogenerate -m "add readres"`
and to update database
`alembic upgrade head`

----
Now we will make a function to create a reader
in `main.py`:
```python
@app.post("/readers/")
async def create_book(request: Request):
    data = await request.json()
    query = readers.insert().values(**data)
    last_record_id = await database.execute(query)
    return {"id": last_record_id}
```

in Postman
- add request "create reader" -  *post* request
- url: `http://127.0.0.1:8000/readers`
- Headers: key-`Content-Type`, value-`application/json`
- Body (raw) `{"first_name:"...", "last_name":"...."}` and send it 
- 

## Many-to-many
We want: a reader reads many books and a book can be read by many readers

We change table structures and add a new one:
```python

books = sqlalchemy.Table(
    "books",
    metadata,
    sqlalchemy.Column("id", sqlalchemy.Integer, primary_key=True),
    sqlalchemy.Column("title", sqlalchemy.String),
    sqlalchemy.Column("author", sqlalchemy.String),
    sqlalchemy.Column("pages", sqlalchemy.String),

)
# .ForeignKey("table_name")
# index=True because we may want to search in books table for reader_ID

readers = sqlalchemy.Table(
    "readers",
    metadata,
    sqlalchemy.Column("id", sqlalchemy.Integer, primary_key=True),
    sqlalchemy.Column("first_name", sqlalchemy.String),
    sqlalchemy.Column("last_name", sqlalchemy.String),
)

readers_books = sqlalchemy.Table(
    "reader_books",
    metadata,
    sqlalchemy.Column("id", sqlalchemy.Integer, primary_key=True),
    sqlalchemy.Column("book_id", sqlalchemy.ForeignKey("books.id"), nullable=False),
    sqlalchemy.Column("reader_id", sqlalchemy.ForeignKey("readers.id"), nullable=False),
)

```
so
we have to make migration: `alembic revision --autogenerate -m "mirror many many"`
now upgrade database `alembic upgrade head`


now create a new endpoint responsible for reading the book
```python
@app.post("/read")
async def read_book(request: Request):
    data = await request.json()
    query = readers_books.insert().values(**data)
    last_record_id = await database.execute(query)
    return {"id": last_record_id}
```


## to protect data - `.env` file
`DATABASE_URL = "postgresql://postgres:root@localhost:5432/store"` this code in the `main.py` is not secure

In your project in the main path create a new file `.env`
in the file you are going to create a coubple of variables
```.env
DB_USER=postgres
DB_PASSWORD=root

```

now you have to install  a new library:
`pip install python-decouple`

to `main.py` add:
`from decouple import config`









