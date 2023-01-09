[[_0 Learn FastAPI by building a complate project]]


# Schemas (pydantic models)
## skeleton
#pydantic 
a new pycharm project
to work with db: asyncpg, psycopg2, psycopg2, alembic, python-decouple, sqlalchemy, databases
```shell
pip install fastapi
pip install databases
pip install uvicorn
pip install asyncpg 
pip install psycopg2-binary
# (pip install psycopg2 <--doesn't work, but in the new Ubuntu is OK)
pip alembic
pip install sqlalchemy
pip install python-decouple
```

create a `.env` file for a db credential
```
DB_USER=postgres
DBPASSWORD=...
```

now migrate your project (first start Postgres)
`alembic init migrations`
go to `alembic.ini` and find `sqlachemy.url = ...`
got to `migrations/env.py`:
	- `from main import metadata`
	- `target_metadata = metadata`

now do some migration: `alembic revision --autogenerate -m "initial migration"`

now upgrade: `alembic upgrade head`

## Input(request) schema for user sign in
>[!schemas]
>they are nothing more than a simple cross that should inherit from base model
#### `from pydantic import BaseModel`
```python
# ...

class BaseUser(BaseModel):
    email: str
    full_name: str

# a request schema -> ada `In`
# a response schema -> add `Out`
class UserSignIn(BaseUser):
    password: str

# ...
```

To use them define endpoints
```python

@app.post("/register/")
async def create_user(user: UserSignIn):
    # `user.dict()` converts the user object into a user dictionary
    q = users.insert().values(**user.dict())
    id_ = await database.execute(q)
    return
```

`http://127.0.0.1:8000/docs`

## Validation with method class
`pip install email-validator`
`from email_validator import validate_email as validate_e`

```python
class BaseUser(BaseModel):
    email: str
    full_name: str

    @validator("email")
    def validate_email(cls, v):
        try:
            validate_e(v)
            return v
        except EmailNotValidError:
            raise ValueError("Email is not valid")

    @validator("full_name")
    def validate_full_name(cls, v):
        try:
            first_name, last_name = v.split()
        except Exception:
            raise ValueError("You should provide at least 2 names")
```

## Validation with custom field






