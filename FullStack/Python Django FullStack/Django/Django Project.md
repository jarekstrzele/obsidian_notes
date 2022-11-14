[[_ start with Django]]



---
# Django Project
> ==a Django Project== is a collection of applications and configurations that when combined together will make up the full web application

> ==a Django Application== is created to perform a particular functionality for your entire web application. For example you could have a registration app, a polling app, comments app, etc.
> THese Django apps can then be plugged into other Django Projects, so you can reuse them

>[!Create an Django App]
`python manage.py startapp first_app`

----
### Files in the app
- `__init__.py` python know that this directory can be treated as a package
- `admin.py` you can register your models here which Django will then use them with Django's admin interface
- `apps.py` here you can place application specific configurations
- `models.py` here you store the application's data models
- `tests.py` here you can store test functions to test your code
- `views.py` this is where you have functions that handle requests and return responses
- folder `migration` stores databases specific information as it relates to the models

---
### What next?
1. Tell Django that we have just created this app 
	in `settings.py` => 
	```python
		INSTALLED_APP = [ 
		...,
		'first_app'
		]
	```


2. **Create view** and map it to a URL
in the folder of this app `views.py` add



```python
# import http object 
from django.http import HttpResponse

# this is one of many possible views
# any view takes at least one arg -> 'request'
def index(request):
	return HttpResponse("Hello World!")
```

and now we must map this view to URL
so
in the main follder `urls.py` add
```python
from first_app import views

urlpatterns = [
	url(r'^$', views.index, name='index' ),
	url(r'^admin/', adminsite.urls)
]
```

==but I had to update this code==
-> [[Django views]]
- in app add `urls.py`
```python
   from django.urls import path
   from . import views
   
   urlpatterns  = [
       path('first_app/', views.index)
   ]
```
If you write `http://localhost:8000/first_app/`, the browser call `index` function

----







