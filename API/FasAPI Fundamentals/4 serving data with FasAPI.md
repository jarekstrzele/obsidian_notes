[[_ 0 fast API  Fundamentals]]
#api

---

# Serving Data with FasAPI

## Query parameters
by default are required
```python
@app.get("/")
def welcome(name):
    """return a friendly welcome msg"""
    return {'message': f'Welcome {name} to the car sharing service!'}

```
`http://localhost:8000/?name=jarek`
`name=jarek` - request parameter

>[!note]
>If you create a REST API, it's common to prefix your URL with API
```python
@app.get("/api/cars")
def get_cars():
    return db
```

the `app.get` annotation turns this function into a FastAPI operation (there will be a URL `/api/cars` that we can visit our browser and see the result of this function ; such as URL is also called ==endpoint== #endpoint)

### Optional query params with `None`
**filtering**
#fastapi/filtering
```python

@app.get("/api/cars")
def get_cars(size=None):
	if size:
	    return [car for car in db if car["size"] == size]
	return db
```
`size` is optional
the client can add a question mark after the URL and then pass the size of the argument `size`
`http://localhost:8000?size=3`


### Typed Parameters
```python

@app.get("/api/cars")
def get_cars(size: str, doors: int)->list:
    result = db
    if size:
        result= [car for car in db if car["size"] == size]
    if doors:
        result= [car for car in db if car["doors"] == doors]
    return result
```

`doors: int` this hint FastAPI use to convert a string value of `door` to `int` and validate (check weather the value is `int`)

from pure Python point of view adding hints changes nothing (python ignores your type hints)
but FastAPI does read these hints and uses them for all kinds nifty stuff -> most importent:
- validate user input
- contert it to the right type

> 
> about hint "Python: Best Practices for Code Quality"
> 

to make these params optional in Python 3.10:
`def get_cars(size: str|None, doors: int|None)->list:`
in older version:
```python
from typing import List, Optional
@app.get("/api/cars")
def get_cars(size: Optional[str]=None, doors: Optional[int]=None)->List:
    result = db
    if size:
        result= [car for car in db if car["size"] == size]
    if doors:
        result= [car for car in db if car["doors"] == doors]
    return result

```
``
## Path parameter
CANNOT BY OPTIONAL!!!!!
```python
@app.get("api/vars/{id}")
def car_by_id(id):
    result = [car for car in db if car['id'] == id]
    return result[0]
    
```
FastAPI takes the value of id parameter from the path of the URL

to run script by itself:
```python
if __name__ == "__main__":
	uvicorn.run("carsharing:app", reload=True)
```

```python
@app.get("/api/cars/{id}")
def car_by_id(id: int) -> dict:
    result = [car for car in db if car['id'] == id]
    if result:
        return result[0]
    else:
        raise HTTPException(status_code=404, detail=f'No car with id={id}.')

```


## Type Hints
Python 3.6, It is used by FastAPI to:
- conversion
- validation
- documentation
- not work with the return type





