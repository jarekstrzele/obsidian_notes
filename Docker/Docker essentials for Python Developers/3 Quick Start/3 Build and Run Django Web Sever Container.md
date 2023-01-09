[[_intro quick start docker]]



----
# Build and Run Django Web Sever Container

### django1
`docker run -it --name mydjango1 -p 8000:8000 -v ${PWD}:/app python:3.8 bash`

`pip install django==2.2.6`

in the container:
`cd /app`
`django-admin startproject testsite`

`cd testsite`
`python manage.py runserver 0:8000` (0:8000 because we start django in the container)

stop a server (ctr+c)

CREATE a django app:
`python manage.py startapp app1`

In the container you are a root user.
In the host you are not a root user.
You have to change ownership as a host root user:
`sudo chown -R jarek:jarek testsite`


in the app view add:
```py
from django.shortcuts import render
from django.http import HttpResponse


def index(request):
    return HttpResponse("Hello! I run in a Python Runtiome COntainer")
# Create your views here.
```


in the app folder add 'urls.py'
```py
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name="index"),
]

```

in the project file `urls.py` add:
```py
urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('app1.urls')),
]
```


You can start this project in other container:
`$ docker run -it --name mydjaongo-beta -p 8000:8000 -v ${PWD}:/app python:3.8 bash`

---







