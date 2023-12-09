#django

[[2 Building a Data Model]]
[[3 Setting Up the Database]]
[[4 Django ORM]]
[[5 the Admin Site]]


# Intro Django
> Django is a free and open-source framework for building web apps with Python

[[Debugging Django App in VSCode]]


**URL** Uniform Resource Locator - this is a way to locate a resource on our internet (resource: page, img, video, ... )

by HTTP (HyperText Transfer Protocol):
>client  --- request     ---> server 
server --- response ----> client


>**BEST PRACTICE**
>Push the responsibility of generating web pages to the client

#endpoint 
so the server becomes a gateway to the data
On the server, we can provide endpoints that the client can talk to, to get or save various prieces of data -> examples of ENDPOINTs:
- `/product`
- `/orders`
- ...
this set of endpoints is a API, Application Programming Interface
e.g. React can talk to a Django server by these endpoints

---
Environment
- `pip3 install pipenv`
- VS Code
- `mkdir storefront`
- `cd storefront`
- `pipenv install django`

(I use `MyDjangoEnv/bin/activate`)

```bash
$ django-admin startproject storefront
```

the current directory will be the project directory
```bash
$ django-admin startproject storefront .
```

```bash
$ python3 manage.py runserver
...
Django version 4.0, using settings 'storefront.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
...
```


View> Command Palett (crt+shift+p) => wybierz interpreter z wirtualnego środowiska, więc włączenie terminala automatycznie uruchamia  środowisko wirtualne


## APPS
#django/app
Django project is:
- a collection of apps
- each apps provide a certain functionality

to create app
```bash
$ python3 manage.py startapp playground
```
`apps.py` is a config file for that app


You have to register this new app:
- `settings.py` in the core folder 
- `INSTALLED_APP... 'playground' ..`


----------
## Views
#django/view 
We use Views in HTTP context.
In our app there is a file `views.py`
```python
from django.shortcuts import render
from django.http import HttpResponse

def say_hello(request):
	return HttpResponse('Hello World')
```

## Mapping URLs to Views
Make in your app folder a new file `urls.py`
```python
from urllib.parse import urlparse
from django.urls import path
from . import views

urlpatterns = [
path('hello/', views.say_hello)
]
```

and in the core `urls.py`
```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
	path('admin/', admin.site.urls),
	path('playground/', include('playground.urls'))
]
```

## Templates
templates return HTML content to the client
in the app `playground` > create a folder `templates` > create a file `hello.html`
```html
<h1>Hello {{ name }} </h1>
```

in `views.py`
```python
from django.shortcuts import render
from django.http import HttpResponse

def say_hello(request):
	return render(request, 'hello.html', {"name":"jaro"})
```

------
# Debugging
in VSCode  (debug button) -> create `launch.json` (now VS code knows how to run or debug this application)
















