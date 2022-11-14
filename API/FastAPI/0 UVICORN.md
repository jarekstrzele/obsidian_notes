
https://www.uvicorn.org/

# Uvicorn
Uvicorn is an [[ASGI]] web server implementation for Python.

`pip install uvicorn` minimap dependecies

`pip install uvicorn[standard]` with "Cython-based" dependecies:
	- `uvloop` installed and possible to use
	- `httptools` the http protocol will be handeld
	- `h11`

## run
`uvicorn.run` in terminal

```python
# main
import uvicorn
async def app(scope, receive, send):
	...

if __name__ = "__main__":
	uvicorn.run("main:app", port=5000, log_level="info")
```




