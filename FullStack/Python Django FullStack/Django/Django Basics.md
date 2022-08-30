[[_ start with Django]]


----
# Basic Django
When you install Django, it actually also installed a command line tool called: `django-admin`.

TO CREATE a PROJECT type:
`django-admin startproject first_project`

`conda activate MyDjangoEnv`

----
in docker 
```Dockerfile
FROM python:3.10-slim

RUN pip3 install django

WORKDIR /app
COPY ./first .

EXPOSE 8000
CMD ["python3", "manage.py", "runserver", "0:8000"]
```

`docker build -t my_django .`
`docker run -it --name my_first -p 8000:800 my_django`

----
## AFTER creating project
`__init__.py` this is a blank Python script that due to its special name let's Python know that this directory can be treated as a package

`settings.py`  this is where you will store all your project settings

`urls.py` this is a Python script that will store all the URL patterns for your project. Basically the different pages of your web application

`wsgi.py` this is a Python script that acts as the Web Sever Gateway Interface. It will later on help us deploy our web app to production

`manage.py` this is a Python script that we will use a lot. It will be associates with many commands as we build our web app

`python manage.py runserver`

---
## MIGRATION
#django/migration
- a migration allows you to move databases from one design to another, this is also reversible
- so you can "migrate" your database















