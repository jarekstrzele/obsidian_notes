#fastapi #python #plurasight #ekker_jan 
#restapi #api 


[[4 serving data with FasAPI]]
[[5 Serving Strucutred Data using Pydantic Models]]

----
# Intro FastAPI
to run script by itself:
```python
if __name__ == "__main__":
	uvicorn.run("carsharing:app", reload=True)
```

REST api with FastAPI
https://fastapi.tiangolo.com/

**FastAPI**
- young
- focused on REST
- minimal code
- performance
- type hits
- validation, conversion of data
- auto-generated docs

**Django**
- very mature
- very complete
- focused on websites
- extension:django-rest-framework

**Flask**
- microframework - almost no features
- focused on websites
- use extensions or write your own 
- 

-----
# First steps
[[_ 0 FastAPI]]
[[_ 0 start REST API i python]]

`python3 -m venv project_name`
`source project_name/bin/activate`
`pip3 install "fastapi[all]"` - install all dependencies (e.i univcorn)

*carsharing.py*:
```python
from fastapi import FastAPI

app = FastAPI()

# there is a connection between URL and function name
# when a GET request comes in for "/", the function will be called
@app.get("/")
def welcome():
    """return a friendly welcome msg"""
    return {'message': 'Welcome to the car sharing service!'}


```

`uvicorn file_name:application_name --reload`
`uvicorn carsharing:app --reload`

`localhost:8000/docs`
`http://localhost:8000/redoc`

`127.0.0.1:60146 - "GET / HTTP/1.1" 200 OK` - GET request was received for this path
`welcome` function - mapped -> `/`, 
so FastAPI looks up the operation mapped to that path (when `/` execute function `welcome`)

> [!control flow]
> Control flow is dectated by incoming HTTP Requests 
> an operation is only called if its URL is requested (so every time when you refresh the page, a new request will be generated
```shell
INFO: 127.0.0.1:60164 - "GET / HTTP/1.1" 200 OK
INFO: 127.0.0.1:60166 - "GET / HTTP/1.1" 200 OK
INFO: 127.0.0.1:60168 - "GET / HTTP/1.1" 200 OK
INFO: 127.0.0.1:60168 - "GET / HTTP/1.1" 200 OK
```
----
# `async`
#python/async
see documentation: https://fastapi.tiangolo.com/async/

		`async    await`

==FastAPI supports asynchronous functions==

`async def ....`
>[!important]
>You can only use await inside of functions created with async def.















