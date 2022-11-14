[[_ 0 FastAPI]]


---
# Routers
>[!routers]
>- a way to structure your application into different files and different components
>- allow us to split our app and our operations that we have on our API into multiple files and the multiple comonents
>- allow us:
>	- separate operations into multiple files
>	- share a pretix btw multiple operations
>	- share tags btw (between) multiple operations

```python
from fastapi import APIRouter
router = APIRouter(prefix='/blog', tags=['blog'])

@router.get('/')
```

and than user your router into your app
```python
from routers import blog
app = FastAPI()
app.include_router(blog.router)
```


## refactoring the app
1. make a folder `routers`
2. inside this folder `blog_get.py`
```python
from typing import Optional
from fastapi import APIRouter, status, Response
from enum import Enum

router = APIRouter(
    prefix='/blog',
    tags=['blog']
)
```
1. remove `get` methods from `main.py` to this file and make some changes"
	1. delete `'/blog'` in all methods (you uses `prefix` in the router)
	2. delete `tags=['blog']` in all methods (you use `tags=['blog']` in the router
2. in `main.py`
```python
from fastapi import FastAPI
from router import blog_get

app =FastAPI()
app.include_router(blog_get.router)

@app.get('/') # using my app to create get method on the home endpoint
def index():
    return 'Hello world twice'
```



## adding a new router with post
1. in ther `router` folder create a new file `blog_post.py`
```python
from fastapi import APIRouter 

router = APIRouter(
    prefix='/blog',
    tags=['blog']
)


@router.post('/new')
def create_blog():
    pass 

```

in`main.py`
```python

```



