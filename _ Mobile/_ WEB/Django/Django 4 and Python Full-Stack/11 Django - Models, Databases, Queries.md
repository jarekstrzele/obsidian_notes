#django 
[[_ 0 Django 4]]

# Django - Models, Databases, Queries

![[working django.excalidraw | 700]]


>[!definition] Models
>Models allow us to interact with a database with Python and Django
>CRUD
>They are defined inside a Django app (or project) `models.py` file
>The models class operates on a system which directly converts Python based code into SQL commands
>Creating a Model is similar to creating a new table in a database
#django/models

## Databases
Django Models is designed to work really well with a tabular SQl based format

## Models and Databases
Inside of `models.py`:
```python
from django.db import models

class Person(models.Model):
	first_name = models.CharField(max_length=30)
	last_name = models.CharField(max_length=30)
```
this code will be automatically converted to SQL:
```sql
CREATE TABLE myapp_person(
	"id" serial NOT NULL PRIMARY KEY,
	"first_name" varchar(30) NOT NULL,
	"last_name" varchar(30) NOT NULL
);
```

==DJANGO MODEL KEY CONCEPTS==
- inherits from **models** class
- uses **fields** to define both data **types** and data **constraints**
- Django Models can also be connected through keys
```python
from django.db import models

class Musician(models.Mode):
	first_name = models.CharField(max_length=50)
	last_name= models.CharField(max_length=50)
	instrument = models.CharField(max_length=50)

class Album(models.Mode):
	artist = models.ForeighKey(Musician, on_delete=models.CASCADE)
	name= models.CharField(max_length=50)
	release_date = models.DateField()
```
	
## Models and Fields
#django/fields





