[[_ 0 FastAPI]]


---

# Operation description

It is very important.


## status code
a request was successful? ...
HTTP  status code

*status object* and *Respons*
`import fastapi import FastAPI, status, Response`

```python

@app.get('/blog/{id}', status_code=status.HTTP_200_OK)
def get_blog(id: int, response: Response): # response is passed automatically
    if id > 5:
        response.status_code = status.HTTP_404_NOT_FOUND
        return {'error':f'Blog {id} not found'}
    else:
        response.status_code = status.HTTP_200_OK
        return { "message": f"Blog with id {id}"}
```


## tags
They allow us to structure and organize our operations within a single file, so we are able to categorize operations based on the string that we provide in the tags (==multiple categories are possible==)

`@app.get('/blog/{id}/comments/{comment_id}', tags=['blog', 'comment'])`

```python
@app.get(
    '/blog/all',
    tags=['blog']
    )
def get_all_blogs(page=1, page_size=10):
    return {'message': f'All {page_size} blogs on page {page}'}
```

## summary and description

**summary** is very brief (a few words)
**description** is usually a larger text
How
==first way==
```python
@app.get(
		 '/blog/all',
		 tags=['blog'],
		 summary="retrieve all blogs"
		 description="This api call simulates fetching all blogs"
)
```

==second way:==
Description is also taken from function `docstring`
```python
@app.get('/blog/{id}/comments/{comment_id}', tags=['blog', 'comment'])
def get_comment(id: int, comment_id: int, valid: bool = True, username: Optional[str] = None):
    """ 
        Simulates retrieving a comment of this blog

    - **id** mandatory path parameter
    - **comment_id** mandatory path parameter
    - **valid** optional query parameter
    - **username** optional query parameter
    """
    return {'message': f'blog_id {id}, comment_id {comment_id}, valid {valid} user name { username }'}
```

## response decription
info about the output

```python
@app.get(
    '/blog/all',
    tags=['blog'],
    summary='Retrieve all blogs',
    description='This api call simulates fetching all blogs',
    response_description="The list of available blogs"
    )
def get_all_blogs(page=1, page_size=10):
    return {'message': f'All {page_size} blogs on page {page}'}
```















