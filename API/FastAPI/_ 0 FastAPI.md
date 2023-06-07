#python #api #fastapi #udemy 
#catalin_stefan


---
# Start FastAPI
[[3 - GET Method]]
[[4 - operation description]]
[[5 - Routers]]
[[6 - Parameters]]
[[7 Database with SQLAlchemy]]

---
- the fastest growing API framework
- easy to use
- fast
- lightweigt
- Swagger doc feature is awesome
	- every endpoint that you develop is automatically translated to documentation 

---
## installation

1. install python
2.  globally `pip install fastapi `
3. in virt environ `python3 -m venv fastapi-venv` next in the new folder `fastapi-venv/bin` is a file (on windows not bin by Script) `activate` (on windows `activate.bat`) `$ source fastapi-venv/bin/activate`
4.  `pip3 install fastapi`
5. install server that allos us to make our endpoints available on our local machine `pip3 install uvicorn`

```python
from fastapi import FastAPI

app =FastAPI()

@app.get('/') # using my app to create get method on the home endpoint
def index():
    # return 'Hello world'
	# better json
	return {"message": "Hello json world"}
```
in the terminal you have to run a server:
`$ uvicorn main:app --reload` (in the file `main` the server will find an fastapi object `app`)
(`--port 8001`)
`localhost:8000`
**operations**:
- get
- post
- ...

----
## Features
- automatic documetation
	- Swagger:  `localhost:8000/docs` -> automatically generated endpoint of docs or
	- ReDoc the spider UI `localhost:8000/redoc`
- standard python3 
- security and authentication
- dependency injection
- testing - 100% coverage



