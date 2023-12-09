[[_ 0 Django 4]]

a VS Code plugin:
#plugin 
Django
Baptiste Darthenay




# Intro to Django
#django4 

## Django:
- backend 
- 2004 Adrian Holovaty
- 2008 non-profit Django Software Foundation
- very good online documentation 
- Python based framework for creating web apps
- provides rules, strucs, functionality that allows us to use Python code and libraries on the back end of our web app

## Why use Django?
- allows for fast development
- many common features included
- updated often and scure
- very scalable
- very versatile with Python
- it has "batteries included" (modules that take care of really common web app features
	- built-in functionality: administration, authentication, database interaction, security
	- all Python libraries can be used in Django

==some cons==:
- Django has so many features, so there is sometiems a bit of a steep learining curve
- it may include many features you don't intend on using
- built with Python (first Python, later Django)

## How Django works?
### Key features of Django:
- Model-Template-View (MTV) Structure
	- ORM - Object-relational Mapper
	- Models
	- URLs and Views
	- Templates
	- 
 ==template== itself is an HTML file (html, css, js)
==jinja== `{{ ... }}` allows us to insert information directly from a python file into that template
`view.py` this python file is esentially a list of functions and the use of decorators (it's going to allow us to inject information into that template directly from Python); 
	- this file woks in concert with some URL routing  `urls.py`
	- this file is often linked to a model
`urls.py` it just tells which view goes to which URL route 
==model== is a Python representation of a database and database tables, it is a python class where attributes <=> columns within a table within DB


![[working django.excalidraw | 700]]

### Django Drawbacks
- heavily reliant on idea of Model
- the model is a Python representation of a table in a database
- this makes it very easy to work with querying data, but does add the requirement of understanding Models and setting them up for views


## First project
`django-admin` automatically create a set of subdirectories and files for us

### `django-admin startproject project_name`

### `django-admin startproject proj_name .`

this creates:
- `project_name` a top level directory, container for project, you can rename this folder
	- `project_name`
		- `__init__.py` (info for Python that this folder is a package)
		- `settings.py` settings for entire Django project
		- `urls.py`
		- `asgi.py` entry point for server
		- `wsgi.py` entry point for server
	- `manage.py` allows to interact with Django project

`python3 manage.py runserver` to run a server on 8000 port
`python3 manage.py runserver 8080` to run a server on 8080 port


## First app
>[!important] Django Project, Apps
>- it can have separated components called "apps"
>- "web app" describes the full website or mobile application on the web
>- a "django app" is a subcomponent of a single Django Project (web app)
>-  each app should cover a different key functionality for your website

Being in the same folder as `manage.py` 
#### `python3 manage.py startapp app_name`
this command doesn't create a `urls.py`

![[django_project_app_urls.excalidraw | 700]]

in `my_app` folder:
`view.py` 
```python
from django.shortcuts import render
from django.http import HttpResponse

def index(request):
    return HttpResponse("Hello this is a view inside my app")
```

create file `urls.py`:
```python
from django.urls import path
from . import views

urlpatterns=[
path('', views.index, name="index") #/my_apps --> PROJECT urls.py
]
```
now open `urls.py` in `my_site` folder (this is the forlder created during creating a Django project)

on projet level in the *urls.py*
```python
from django.contrib import admin  
from django.urls import path,include  
  
urlpatterns = [  
    path('my_app/', include('my_app.urls')),  
    path('admin/', admin.site.urls),  
]
```

`$ python manage.py runserver`






