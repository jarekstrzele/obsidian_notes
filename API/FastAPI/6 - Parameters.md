[[_ 0 FastAPI]]


------
# Parameters


## Request body
How we can receive information in a post request and what kind of information we can receive?

We want to send some info within the body of the request to an API, and our API must be retreived that info and process it


### Post method Request body
In  post we don't send all the info that we have in the query params, we send more detailed info inside the body of the request
for this purpose FastAPI uses `pydantic` (to convert data between JSON and the model that we have in our FastAPI ), so we have to use `BaseModel` from `pydantic` and extend this class 

Pydantic *BaseModel*
```python
class BlogModel(BaseModel):
	title: str
	content: str
	published: Optional(bool)
```
==FastAPI will convert the data from the request, which contains JSON into our class==

FastAPI will convert the data:
```python
@router.post('/new')
def create_blog(blog: BlogMode):
	return blog
```

**Request body**
- read request body as JSON
- data validation
- data conversion
- JSON schema


## Path and Query parameters
How do we mix and match different types of parameters in our request and how we can make the separation between them?
`def create_bog(blog: BlogModel, id: int): ...`
**body params** type of parameter that inherits from `BaseModel` (`blog`)
**query params** primitive types of params (`id`)

```python
from re import S
from typing import Optional
from fastapi import APIRouter
from pydantic import BaseModel 

router = APIRouter(
    prefix='/blog',
    tags=['blog']
)

class BlogModel(BaseModel):
    title: str 
    content: str 
    published: Optional[bool]

@router.post('/new/{id}/')
def create_blog(blog: BlogModel, id: int, version: int = 1):
    return {
        'id': id,
        'data': blog,
        'version': version
    }
```
`id` is a path param
`version` is a query param


## Parameter metadata
metadata is  data bount the data (information about our parameters)
- metadata -> info displayed in docs
- you can attach metadata using the Query, Path, and Body imports
`from fastapi import Query, Path, Body`

- add title and description:
```python
commnet_id: int = Query(None, 
			title="Id of the comment",
			description='Some description for comment_id')
```

- add alias
```python
comment_id: int = Query(None, alias='commentId')
```

- add deprecation
```python
comment_id: int = Query(None,
			deprecated=True)
```

```python

@router.post('/new/{id}/comment')
def create_comment(blog: BlogModel, id: int, comment_id: int =Query(
    comment_id= "Id of the commnet",
    description="Some description for comment_id",
    alias="commentid",
    deprecated=True
    )):
    
    return {
        'blog': blog,
        'id': id,
        'comment': comment_id
    }
```



## Validators
How we can validate our data even before we start processing it in our function

- Provide a default value:
	`content: str = Body('Hi')` this is optional
- require a value (non-optional params):
	`content: str = Body(...)` (or `content:str = Body(Ellipsis)`) this is required 
- require minimum/max length
	`content: str = Body(..., min_length=10)`
	`content: str = Body(..., max_length=20)`
- require regex:
	`content:str Body(..., regex=regex)`
	`regex = ^[a-z\s]*s`

## Multiple values 
How we can get multiple values for our parameters? (list, array)
==only for query params==
`localhost:8001/blog/new/2/comment?commentId=4&v=1.0&v=1.1&v=1.2&v=3`

Define an optional query parameter:
`v: Optional[List[str]] = Query(None)`

Provide default values:
`v: Optional[List[str]] = Query(['1.0', '1.1', 1.2'])`

### Number validators
Greater than
	`comment_id: int = Path(None, gt=5)`

Greater than or equal to
	`comment_id: int = Path(None, ge=5)`

Less than `lt=`
less than or equal `le=`

```python

@router.post('/new/{id}/comment/{comment_id}')
def create_comment(blog: BlogModel, id: int, comment_title: int =Query(
    comment_title= "title of the commnet",
    description="Some description for comment_title",
    alias="commentTitle",
    deprecated=True
    ),
    content: str = Body('hi how are you', min_length=10),
    v: Optional[List[str]] = Query(['1.0', '1.2', '2.0']),
    comment_id: int = Path(None, gt=5, le=10)
    ):
    
    return {
        'blog': blog,
        'id': id,
        'comment': comment_title,
        'content': content,
        'version': v,
        'comment_id': comment_id
    }

```


---
## Complex subtypes
to be able to receive information not only basic (Bool, str, int, ...) but also our own types of data

Pydantic models are not restricted to simple types:
`tags: List[str] = []`

List, set, dict, tuple:
`metadata: Dict[str, str] = {"key1": "val1"}`

Custom model subtypes
```python
class Image(BaseMode):
	url: str
	alias: str

image: Optional[Image] = None
```

```python

class Image(BaseModel):
    url: str
    alias: str

class BlogModel(BaseModel):
    title: str 
    content: str 
    published: Optional[bool]
    tags: List[str] = []
    metadata: Dict[str, str] = {'k1':'v1'}
    image: Optional[Image] = None


```








