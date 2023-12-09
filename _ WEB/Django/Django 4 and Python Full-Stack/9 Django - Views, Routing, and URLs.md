[[_ 0 Django 4]]

#django 

# Django - Views, Routing, and URLs

### connectiong a View with a URL
>[!important] **Views**
>dictate WHAT information is being shown to the client

>[!important] **URLs**
>dictate WHERE information is  shown on the website  
>its configuration can be on Project level or App level
>`path()` and `include()`
>`urlpatterns` a list of view routes


View/URL as a web page on the website
URLs and Views support dunamic and logic features


## Connection a View to a URL with `path(route, view)`:
- **route** 
	- string code that contains the URL pattern
	- Django will scan the relevant ==urlpatterns== list until it findes a matching string route (e.g. "app/")
- **view** 
	- once a matching route is found, the view argument connects to a function or view, typically defined tn the **views.py** file to the relevant Django app
- OPTIONAL ARGS
	- **kwargs** allow us to pass in keyword args as a dictionary to the view
	- **name** allows us to name a URL in order to reference it eslewhere in Django

---
## Function `Views` basics
#django/view
our project:
- `my_site` is a project lever
- `first_app` is the first app in this project
so 
in the `first_app` create a new file `urls.py` and this will control the URLs that are associated with views inside  of first app
this file will be connected to the project level URLs 

On the project level you definde:
`path('first_app/', include('first_app.urls'))`
and on the first_app level you write
`path('', views.simple_view)` the first argument of this function (`''`) will be added  to the urls, so this empty string ->
`first_app/`


in `first_app` in `views.py`
```python
from django.http.response import HttpResponse  
  
  
def simple_view(request):  
    return HttpResponse("Simple VIEW")
```

in `first_app` in `urls.py`
```python
from django.urls import path  
from . import views  
  
urlpatterns = [  
    path('', views.simple_view),  
]
```

in `my_site` in `urls.py`:
```python
from django.contrib import admin  
from django.urls import path, include  
  
urlpatterns = [  
    path('admin/', admin.site.urls),  
    path('first_app/', include('first_app.urls'))  
]
```

---
## Dynamic Views - Rounting Logic
### two key ideas:
- adding in logic to a View
- creating dynamic Paths (URL Path Routes defined by the client)

in `first_app`
	in `views.py`
```python
from django.shortcuts import render  
from django.http.response import HttpResponse  
  
articles = {  
    'sports': 'Sports Page',  
    'finance': 'Finance Page',  
    'politics': 'Politics Page'  
}  
  
  
def news_view(request, topic):  
    return HttpResponse(articles[topic])  
  
def add_view(request, num1, num2):  
    add_r = num1 + num2  
    result = f'{num1}+{num2} = {add_r}'  
    return HttpResponse(str(result))
```

	in `urls.py`
```python
from django.urls import path  
from . import views  
  
urlpatterns = [  
    path('<str:topic>/', views.news_view),  
    path('<int:num1>/<int:num2>', views.add_view)  
]
```

## Responses and 404s
#django/response

- a client requests a web page view that does not exist or
- a client didn't provide the correct URL route
In these cases, we can use `HttpResponseNotFounr()` to still return a webpage for the user

Django has default `404 page` we can display

First way:
```python
def news_view(request, topic):  
    try:  
        result = articles[topic]  
        return HttpResponse(articles[topic])  
    except:  
        result = "No page for that topic!"  
        return HttpResponseNotFound(result)
```


Better way?:
```python
def news_view(request, topic):  
    try:  
        result = articles[topic]  
        return HttpResponse(articles[topic])  
    except:  
        raise Http404("404 Generic error")
```

---
## Redirect basics
#django/redirect
a client provide a pth that we want to redirect to another webpage on our site
this can be accomplished in Django through the use of the `HttpResponseRedirect()` function

```python
# domain.com/first_app/0 ---> domain.com/first_app/sports  
def num_page_view(request, num_page):  
    topics_list = list(articles.keys())  
    topic = topics_list[num_page]  
  
    return HttpResponseRedirect(topic)
```

```python
urlpatterns = [  
    path('<int:num_page>', views.num_page_view),  
    path('<str:topic>/', views.news_view),  
    path('<int:num1>/<int:num2>', views.add_view)  
]
```

but I have some problems because redirected url is `http://127.0.0.1:8000/first_app/0/sports` but should be `http://127.0.0.1:8000/first_app/sports`


----
## Reverse URLs and URL Names
### two key ideas:
- URL Path inside the `path()` function can have **names** tgat can ve referenced across Django and inside of a template
- Django has a `reverse()` function to find the corresponding URL path for a URL **name**
- 

### a typical flow for a webpage
user -> URL -> `urls.py` -> `views.py`
but it also can be:
`views.py` -> `urls.py` when in the `views.py` you use `reverse(url_name)` method


```python
  
urlpatterns = [  
    path('<int:num_page>', views.num_page_view),  
    path('<str:topic>/', views.news_view, name='topic-page'),  
]
```

```python
# domain.com/first_app/0 ---> domain.com/first_app/sports  
def num_page_view(request, num_page):  
    topics_list = list(articles.keys())  
    topic = topics_list[num_page]  
  
    webpage = reverse('topic-page', args=[topic])  
    return HttpResponseRedirect(webpage)
```
but still the same error


---
## Connectiong a View to a Template
We want to separate out all our templates (HTML files) into a separate directory and have views communicate between this directory and render the templates

Connectiong to a template directory requires us to informa the Django project settings where to find these templated

recommended way: store templates on a Django app level

we do:
- create a new templates directory
- create an example.html file
- connect to that .html within the view 
- inform the Django project where to find this template directory inside of `settings.py`

this is not quite correct:
project level (where is `manage.py`) a new directory (`templates`) inside it a new directory `first_app` and in this directory a new file `example.html`

`views.py`
```python
  
def simple_view(request):  
    return render(request, 'first_app/example.html')
```
`urls.py`
```python
urlpatterns = [  
    path('', views.simple_view)  
]
```
but we still don't tell Django about our template, so we have to go to `settings.py` (project level) a part of this file called 'TEMPLATES'
```python
import os
# ...
TEMPLATES = [  
    {  
        'BACKEND': 'django.template.backends.django.DjangoTemplates',  
        'DIRS': [os.path.join(BASE_DIR, 'templates/')],  
        'APP_DIRS': True,  
        'OPTIONS': {
# ...
        
```
























