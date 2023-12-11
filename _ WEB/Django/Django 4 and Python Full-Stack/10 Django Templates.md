[[_ 0 Django 4]]

#django/templates

# Django Templates
to connect out Django views code to template files (HTML,CSS, JS)

## Template Directories
Separate out template directories by app
==We have to register the custom Django app in the `settings.py`
under the INSTALLED_APPS variable.==

### setps:
1. Create App Directory with `python manage.py startapp` command 
	1. create the relevant URLs and Views
	2. map the appURLs to the Project URLs
2. Run the migrate command `python manage.py migrate` this command looks at INSTALLED_APPS in settings and creates any necessary database tables
3. Inside of Django App check the `apps.py` created automatically for you and register the AppConfig class to the INSTALLED_APPS inside f settings.py
   (this step links your project with th app directories)
4. Register the app and any database changes with Django by running `python managepy makemigrations myapp`
5. Run `python manage.py migrate` again to create the model tables in our database
6. Ctreate a templates directory inside your app directory with this structure:
	1. `my_site`
		1. `my_app`
			1. `templates`
				1. `my_app` (this subfolder protect against name confilcts (e.g. many `index.html` files in many Django apps) without this subfolder Django choses the first template that name matches)
					1. `example.html`

---
# New Project

`django-admin creat-project my_site`

## a new app
`python3 manage.py startapp my_app`
in `my_app`
view
```python
from django.shortcuts import render
# Create your views here.
def example_view(request):
	# my_app/templates/my_app/example.html
	return render(request, 'my_app/example.html')
```
urls
```python
from django.urls import path
from . import views

urlpatterns = [
	path('', views.example_view)
]
```

in `my_site`  urls
```python
urlpatterns = [
	path('admin/', admin.site.urls),
	path('my_app/', include('my_app.urls'))
]
```

`python3 manage.py migrate`

## To install this new app
in `my_app` there is a `apps.py`
```python
from django.apps import AppConfig

class MyAppConfig(AppConfig):
	default_auto_field = 
  'django.db.models.BigAutoField'

	name = 'my_app'
```
it converts your CamelCasing name to a your snake_case

go to the `settings.py` in `my_site` of course
to INSTALLED_APP  add `'my_app.apps.MyAppConfig',`
but this doesn't work
you have to write only `my_app` to register your app into the Django project


so now in `my_app` create a folder `template` with a subfolder `my_app` an a new file `example.html`

`python3 manage.py runserver`
`http://127.0.0.1:8000/my_app/`
OK

---
## Variables in Templates
We will render templates and send a context variable to the HTML with the Django Template Language.

Create a `variable.html` in the `templates/my_app` with some text to verify weather everything is all right

add a new view
```python
def variable_view(request):
	return render(request, 'my_app/variable.html')
```

add a new path
```python
urlpatterns = [
	path('', views.example_view),
	path('variable/', views.variable_view)
]
```

---
Changes:
```python
def variable_view(request):
	my_var={'first_name':'Rosaling', 'last_name':'Franklin'}
	
	return render(request, 'my_app/variable.html', context=my_var)
```

add to `variable.html`:
```html
<h2>{{first_name}}</h2>
```
from the views through the `context` you can have an access to `my_var` in the `variable.html`

---
new changes
```python
def variable_view(request):
	my_var={'first_name':'Rosaling',
	'last_name':'Franklin',
	'some_list':[1,2,3],
	'some_dict': {'inside_key':'inside_value'}
}
	
	return render(request, 'my_app/variable.html', context=my_var)
```

```html
<body>
<h1>Variable.html</h1>
<h2>{{first_name}}</h2>
<h3>{{some_list}}</h3>
<h3>{{some_list.0}}</h3> <!-- indexing, 1-->
<h3>{{some_dict.inside_key}}</h3> <!-- inside_value -->
<h2>{# this is a comment #}</h2>
</body>
```

---
## Filters
#django/filter 
https://docs.djangoproject.com/en/4.1/ref/templates/builtins/

>[!definition] Filters
>Filters are built-in modifiers in Django templating that allow you to quickly apply a change to a variable on the template side, rather than in your Pthon script

```python
{{first_name}} # Rosalind
# -->
{{first_name | upper}} # ROSALIND
```

list of some filter:
- upper
- lenght
- capfirst ("django" -> "Django")
- date 
- first (returns hte first item in a list)

you can  join this filter `{{first_name | lower | capfirst}}` first all characters convert to lowercase and next capfirst


----
## Tags - For loop
https://docs.djangoproject.com/en/4.1/ref/templates/builtins/

#django/tags
>[!definition] Tags
>Django Tags are able to provide futher logic at the template in the rendering process
>This includes a lot of functionalities such as for loops, if-else statemetns, linking to URLs

`{% %}` a tag for `for loop`

```html
<body>

<h1>Variable.html</h1>
<ul>
	{% for item in some_list %}
		<li>{{ item }}</li>
	{% endfor %}
</ul>
</body>
```

```html
<body>
<h1>Variable.html</h1>
<ul>
	{% for k,v in some_dict.items %}
		<li>{{k}}, {{v}}</li>
	{% endfor %}
</ul>
</body>
```


---
## Tags - If Else, Elif
You have to use `end` tag
```html
{% if var == True %}
//
{% endif %}
```

```python
def variable_view(request):
	my_var={'first_name':'Rosaling',
	'last_name':'Franklin',
	'some_list':[1,2,3],
	'user_logged_in': False
	}
	return render(request,
	'my_app/variable.html',
	context=my_var
	)
```

```html
<body>
	<h1>If Else Variable.html</h1>
		{% if user_logged_in %}
		<h1>Welcome back you are logged in </h1>
		{% endif %}
</body>
```

other version
```html
<body>
<ul>
	{% for num in some_list %}
		{%if num == 2%}
			<li>Two</li>
		{%else%}
			<li>{{num}}</li>
		{%endif%}
	{% endfor %}
</ul>
</body>
```

Spaces!!
this code generates error
```html
{% if first_name=='Rosalia' %}
```
this code is correct
```html
{% if first_name == 'Rosalia' %}
```

---
## Tags and URL Names in Templates
Using `path()` function we could assign names to URLs
`{% url %}` this is easy way to create links to other pages based on their URL name in urls.py

We have two template files: `example.html` and ``

A new content of `my_app/urls.py`:
```python
from django.urls import path
from . import views

# register the app namespace
# URL NAMES
app_name = 'my_app'

urlpatterns = [path('', views.example_view, name='example'),
path('variable/', views.variable_view, name='variable')
]
```

`example.html`
```html
<body>
	<h1>example template</h1>
	<h2><a href="{% url 'my_app:variable' %}">Click me to go to Variable</a></h2>
</body>
```

---
## Template Inheritance
`{% block %}` thanks of it you can inherit

e.g. `base.html` (project level) the most repetitive elements (nav bar,  footer ....) (`content` is just a name of this block)
```html
<!--...-->
{% block content%}
<base_contetn>
{% endblock}
<!--...-->
```

`other.html`
```html
{% extends "base.html" %}

{% block content %}
<other_contetn>
{% endblock %}
```

on the project level (next to `my_site` and `my_app`) create a new folder `templates` and a file `base.html`:
```html
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>

<body>
  <h1> this is above the block in base.html </h1>
{% block content%}

{% endblock %}
  <h1>THis is below the block in BASE.html</h1>
</body>
</html>
```

now go to the `example.html`
```html
{% extends 'base.html%}
{% block contetn %}
	<h1> this is inside the block in EXAMPLE.html</h1>
{% endblock %}
```

now we have to register 
`settings.py` > TEMPLATES > ``'DIRS'::[os.path.join(BASE_DIR, 'templates')]

----
## Custom Error Templates
Many pages, such as admin or 404 pages have built-in templates provided by Django for your convenience

We have ability to overwrite any of these built-in templates

on the project level > tremplates > a new file `404.html`

in `settings.py`
```python
DEBUG = False
ALLOWED_HOSTS = ['127.0.0.1']
```

1. create `404.html` in `templates` on the project level
2. in the project folder (`my_site`) create `views.py` 
```python
from django.shortcuts import render

def my_custom_page_not_found(request, exception):
	return render(request, '404.html', statous=404)
```
3. in the main `urls.py` (in the project level) add
```python
handler404 = 'my_site.views.my_custom_page_not_found_view'
```


---

## Static Files
#django/static_files
Most project will have static files, such as images, JS, or CSS.
Django can serve these static files through the use of Tags, instead of haveing to refer to a full file path
This is similat ot the `{$ url %} ` tag but using a `{% styatic %}` tag

check in the `settings` 
in INSTALLED_APPS should be `'django.contrib.staticfiles',`
and
```python  
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/3.2/howto/static-files/
# my_app/static/my_app/static_file_name.jpg
STATIC_URL = '/static/' 
```

create in `my_app` a new folder `static` and subfolder `my_app`
In that subfolder save a file.
example.html
```html
{% extends 'base.html' %}
{% load static %}
{% block content %}
	<h1> this is inside the block in EXAMPLE.html</h1>
	<img src="{% static 'my_app/django.jpg' %}" alt='my image'>
{% endblock %}
```




























