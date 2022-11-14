1. [[Django Basics]]
2. [[Django Project]]
3. [[Django Templates]]
4. 

---

# Start with Django
#python/django 

---
In Docker
1. `$ docker run -it --name mydjango22 -p 8000:8000 -v ~/PROG/Billennium/Python_Django_Full_Stack/Django:/app python bash`
2. `pip install django`
3. `python manage.py runserver 0:8000`
4. in host folder `sudo chown -R jarek:jarek testsite`



----
## High level Overview of Django

![[overview_django.excalidraw | 700]]

## Some information
- Django is a free and open source web framework
- It is used by many sites, including Pinterest, PBS, Instagram, ...
- It was created in 2003 (very good docs)


## Virtual environment
with Anaconda:
`conda create name myEnv django` 
to activate `activate myEnv`
to deactivate `deactivate myEnv`

https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html


`conda create --name MyDjango python=3.5`

```bash
~$ conda info --envs
# conda environments:
#
base         *  /home/jarek/anaconda3
MyDjangoEnv 
 /home/jarek/anaconda3/envs/MyDjangoEnv

```

```bash
# To activate this environment, use
#
#     $ conda activate MyDjangoEnv
#
# To deactivate an active environment, use
#
#     $ conda deactivate

```

```bash
(base) jarek@jarek-Lenovo-G700:~$ conda activate MyDjangoEnv
(MyDjangoEnv) jarek@jarek-Lenovo-G700:~$ conda info --envs
# conda environments:
#
base     /home/jarek/anaconda3
MyDjangoEnv           *  /home/jarek/anaconda3/envs/MyDjangoEnv

(MyDjangoEnv) jarek@jarek-Lenovo-G700:~$ conda install django


$ conda install django
```









