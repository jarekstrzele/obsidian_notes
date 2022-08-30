[[_ 0 FastAPI]]


----
# GET method

## Path parameters
> 
> a value/a variable that we can provide inside our path
> 

```python
@app.get('/blog/{id}')
def index(id):
	return {"message": f"Blog with id {id}"}
```

if you want to validate data type:
```python
@app.get('blog/{id}')
def index(id: int):
	return {"message": f"Blog with id {id}"}
```

> FastAPI uses '`Pydantic` to validate the passed params.

the order of functions is important (rule: more generic later)
```python
@app.get('/blog/{id}')
def index(id: int):
	return {"message":f"Blog with id {id}"}

@app.get('/blog/all')
def get_all_blogs():
	retrun {"message" : "all blogs"}
```
this code generates error
but this one - no:
```python
@app.get('/blog/all')
def get_all_blogs():
	retrun {"message" : "all blogs"}

@app.get('/blog/{id}')
def index(id: int):
	return {"message":f"Blog with id {id}"}


```

---
## Predefined Path
Predefined values with `Enum`


```python
from fastapi import FastAPI
from enum import Enum


app =FastAPI()

@app.get('/') # using my app to create get method on the home endpoint
def index():
    return 'Hello world twice'

@app.get('/blog/all')
def get_all_blogs():
    return {'message': 'All blogs provided'}

class BlogType(str, Enum):
    short = 'short'
    story = 'story'
    howto = 'howto'

@app.get('/blog/type/{type}')
# arg `type` will be `BlogType`
def blog_type(type: BlogType):
    return {"message": f"Blog type: {type}"}

@app.get('/blog/{id}')
def get_blog(id: int):
    return { "message": f"Blog with id {id}"}

```

----
## Query parameters
How we can provide query parameters to FastAPI and to out functions?

>[!query params]
> - params that you pass after your path 
> - they are separated by an `&`
> - they are separated from the path by a `?`
> - any function parameters not part of the path

```python
@app.get('/blog/all')
def get_all_blogs(page, page_size):
    return {'message': f'All {page_size} blogs on page {page}'}
```

`page` and `page_size` are query parameters

#### default values
```python
...
def get_all_blogs(page=1, page_size=20) ...
```

query: `http://127.0.0.1:8000/blog/all?page=1&page_size=10'`


#### optional params
```python
from typing import Optional

@app.get('/blog/all')
def get_blogs(page=1, page_size: Optional[int]=None):
	...
```


#### mixing
```python

@app.get('/blog/{id}/comments/{comment_id}')
def get_comment(id: int, comment_id: int, valid: bool = True, username: Optional[str] = None):
    return {'message': f'blog_id {id}, comment_id {comment_id}, valid {valid} user name { username }'}
```




