[[_ Intro Scalable Web Applications with Python, Flask and SQLAlchemy]]

[[Jinja 2]]

---

# PostrgreSQL
Filozofia2!@
ubuntu pgAdmin



# SECTION 4: working with databases
**SQLALCHEMY**  
#python/sqlalchemy
is the Python SQL toolkit and Object Relational Mapper  
that gives application developers the full power and flexibility of SQL  

`pip3 install Flask-SQLAlchemy`
`pip3 install psycopg2-binary ` 

==**PSYCOPG**==  
is a PostgreSQL adapter for the Python programming language.
It is a wrapper for the libpq, the official **PostgreSQL** client library.  
```py
from flask import Flask, request, render_template
from flask_sqlalchemy import SQLAlchemy


app = Flask(__name__)  

# app.config.update(  
# SECRET_KEY='postgres', 
# SQLALCHEMY_DATABASE_URL='<database>://<user_id>: 
  <password>@<server>/<database_name>',  

SQLALCHEMY_DATABASE_URI  ='postgresql://postgres:postgres@localhost/catalog_db', 
SQLALCHEMY_TRACK_MODIFICATIONS=False  

)  

db = SQLAlchemy(app)
...
if __name__ == '__main__': 
	db.create_all() # create all table if they don't exist
	app.run(debug=True)  
```


# create table  
```py
class Publication(db.Model):  

	__tablename__ = 'publication'  
	id = db.Column(db.Integer, primary_key=True)   
	name = db.Column(db.String(80), nullable=False)  

    def __init__(self, id, name):   
		self.id = id  
		self.name = name  

    def __repr__(self):  
		
		return 'The id is {}, Name is {}'.format(self.id, self.name)  

```


## ORM 
#python/orm
```
class Publication(db.Model)  
   |
  \ /   
    -----is maped
              |
             \ /
CREATE table_name( column1 datatyp, column2 datatyp, ...);
```

---
# SECTION 5: CRUD
#python/orm_crud

in the terminal: [[postgres in a terminal]]

class Publication --> 
`pub = Publication(100, "Oxford Publication)  `


**INSERT** DATA INTO A TABLE  
>1. create instances  
>2. add to the session  
>3. commit to db
  
`db.session.add(pub)`
db is a variable refering to the database
`db.session.commit()`
save data in the table----> 
SESSION OBJECT: 
- temporary storage in memory
- like a staging zone  

when we have more object to insert:  

`db.session.add_all([obj1, obj2, obj...])`
`db.session.commit()  `
  
**RELATIONSHIP**  

```py
class Publication(db.Model):

	__tablename__ = 'publication'  

# in the class Book:  # Relationship
	pub_id = db.Column(db.Integer, db.ForeignKey('publication.id')) 

#table.column  
```


**READING DATA**  
`class_name.query.all()  `
e.g.  

__all__
`Book.query.all()  `
--->
pyhon list[Miky's Delivery Service by William Dobelli, The Secret Life of Walter Kitty by Kitty Stiller, ..]

__first__
`Book.query.first()`
---> Miky's Delivery Service by William Dobelli 

__limit___
`Book.query.limit(5).all()`
---> first 5  

__filter__
`Book.query.filter_by(format='ePub').all()`
[Miky's Delivery Service by William Dobelli, The Sacred Book of Kairo by Heidi Zimmerman]

`Book.query.get(1)`
--> get the record primery_key = 1  

__order__ `class_name.query.order_by(class_name.attribute).all()`
e.g.  
`Book.query.order_by(Book.title).all()  `
`Book.query.filter_by(format='Paperback').order_by(Book.title).all()  `
 

### query data from two tables
1. `result = Publication.query.filter_by(name='Broadway Press').first()  `
2. `broadway = Book.query.filter_by(pub_id = result.id).all() `

**updating records**  
1.  query the record select id -> `u = Book.query.get(16) `
2.  override the current value -> `u.format = 'Hardcover'  `
3.  commit to db -> `db.session.commit()  `


**deleting**  
`x = Book.query.get(10)  `
`db.session.delete(x)  `
`db.session.commit()  `

`Book.query.filter_by(pub_id=6).delete()`
---- three itmes will be deleted -> `Publication.query.filter_by(id=6).delete() `
-> db.session.close()  
  

---







