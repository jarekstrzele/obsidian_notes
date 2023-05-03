
[[_ wstęp Django Rest]]

---


# Modele danych i interfejs api
Patrz. aplikacja stworzona w _wstęp Django Rest_ 

w folderze testapp.testapp:
`django-admin startapp todos`

tę aplikację należy dodać do głównej w pliku `settings.py`:
```
INSTALLED_APPS=[ ...
	'todos',
]
```

i teraz w todos w pliku `models.py`:
Object Relational Mapping ORM #python/orm 

```py
class Todo(models.Model):
    name = models.CharField(max_length=256)
    description = models.TextField()
```

aby Django "wiedział", co robić z takim modelem/klasą `Todo` należy zrobić migrację:
`python manage.py makemigrations`

aby dodać nowy model do bazy danych:
`python manage.py migrate`

---
## Django Shell
#python/django_shell

wejście do shella django
`python manage.py shell`

w shellu:
### CREATE
```shell
from todos.models import Todo

In [2]: Todo.objects.create(name="sample todo", description="test descrition")

In [4]: todo2 = Todo.objects.create(name="sample todo 2", description="test description 2")

```

zmieniamy pola w bazie danych, zapisujemy plik sqlite ze zmianami, a w shellu:
`In [10]: todo2.refresh_from_db()`

### FILTER
`Todo.objects.filter(name="zmieniłem to")` -> _QuerySet_

`Todo.objects.all()` -> wszystkie rekordy
`Todo.objects.filter(name__startswith="sa")`
`Todo.objects.get(id=2)`
























