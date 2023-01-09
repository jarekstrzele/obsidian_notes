[[_ 0 FastAPI]]


---
#python/sqlalchemy 


# Database with SQLAlchemy

## Dependencies overview
- Dependencies are basically a way to allow a function to depend on another function
- write some functionality only once and use it in many places (import functionality seamlessly)
`req_param: dict = Depends(required_functionality)`

exapmple:
add a simple function to the `blog_post.py`:
```python
def required_functionality():
    return {'msg': 'Learning FastAPI is important'}
```
in the `blog_get.py`  make some changes:
```python
def get_all_blogs(page=1, page_size: Optional[int]=None,  req_parameter: dict=Depends(required_functionality)):
    return {'message': f'All {page_size} blogs on page {page}' , 'req': req_parameter}
```
it is usefull: to connect to DB, to verify login, ...

---
## Databases
#python/orm 
- FastAPI works well with all relational db
- ORM library (Object Relational Mapping)

**BOILERPLATE code to create db**
```python
from sqlalchemy import create_engine
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy.orm import sessionmaker
 
SQLALCHEMY_DATABASE_URL = "sqlite:///./fastapi-practice.db"
 
engine = create_engine(
    SQLALCHEMY_DATABASE_URL, connect_args={"check_same_thread": False}
)
SessionLocal = sessionmaker(autocommit=False, autoflush=False, bind=engine)
 
Base = declarative_base()
```

In the root path create a new file `requirements.txt`
```txt
fastapi
uvicorn
sqlalchemy
```
and now:
`pip3 install -r requirements.txt`

now new folder  `db` in root path and a new file inside `database.py` (paste into it a boilerplate)

> if it will be a problem, reinstall venv (delete and reinstall)
> `python3 -m venv fastapi-env`

> [!some concepts]
> ==schema== - info (e.i. to create a user )
> ==model== - info from schema plus extra info
> ==server response== - info from model - some info (e.i. password)

in `db` folder add a new file `models.py`
```python
from sqlalchemy.sql.slqtypes import Integer, String
from db.database import Base
from sqlalchemy import Column


class DbUser(Base):
    __tablename__ = 'users'
    id = Column(Integer, primary_key=True, index=True)
    username = Column(String)
    email = Column(String)
    password = Column(String)
```

so your `main.py`:
```python
from fastapi import FastAPI
from router import blog_get, blog_post
from db import models
from db.database import engine

app =FastAPI()
app.include_router(blog_post.router)
app.include_router(blog_get.router)

@app.get('/') # using my app to create get method on the home endpoint
def index():
    return 'Hello world twice'

models.Base.metadata.create_all(engine) 
```
when you start a server, db will be created







