[[_ 0 fast API  Fundamentals]]
#api 

---
# Serving Strucutred Data using Pydantic Models
#pydantic 
In [[4 serving data with FasAPI]] there is a list of dictionary to store data, but now we change this data into OOP.
```python
db = [
    {"id":1, "size":"s", "fuel":"gasoline", "doors":3, "transmission": "auto"}, 
    ...
```



1. Create a file `schemas.py`:
	1. in this file create classes
	2. this file is called `schemas` because classes will define the shape of valid data structures that our API will accept (so class will be like schema)
```python
from typing import Optional
from pydantic import BaseModel

class Car(BaseModel):
    # object of this class can be converted:
    # to dict `object.dict()`
    # to json `object.json()`
    id: int       # required
    size: str     # required
    fuel: Optional[str]=None 
    doors: int    # required
    transmission:Optional[str] = None 

def load_db() -> list[Car]:
    """Load a list of Car objects from a JSON file"""
    with open("cars.json") as f:
        # parse_obj: dict_from_json -> object of Car class
        return [Car.parse_obj(obj) for obj in json.load(f)]


```

In `carsharing.py` import `load_db` from `schemas.py`
```python
app = FastAPI()
db = load_db()
```
and methods have to have OOP syntax:
```python
@app.get("/api/cars/{id}")
def car_by_id(id: int) -> dict:
    result = [car for car in db if car.id == id]
    if result:
        return result[0]
    else:
        raise HTTPException(status_code=404, detail=f'No car with id={id}.')

```

----
## HTTP Methods
#http 

**GET** `/api/cars/5`:
- no side effects
- retrieve data - don't change anything

**POST** `/api/cars`:
- add a new item
- data in body not in the URL

**PUT** `/api/cars/5`
- replace resource: update a car
- data in body

**DELETE* `/api/cars/5`
- remove a car

---
## Adding a new object
```python

def save_db(cars: list[Car]):
    with open("cars.json", "w") as f:
        json.dump([car.dict() for car in cars], f, indent=4)

```

```python
# you can't use these method in the browser
# use `../docs`
@app.post("/api/cars/")
def add_car(car: CarInput) -> CarOutput:
    new_car = CarOutput(size=car.size, doors=car.doors, fuel=car.fuel, transmission=car.transmission, id=len(db)+1)
    db.append(new_car)
    save_db(db)
    return new_car
```
but FastAPI doesn't car of the type of the return value.
To change this 
```python
@app.post("/api/cars/", response_model=CarOutput)
def add_car(car: CarInput) -> CarOutput:
...
```
so FastAPI will validate and convert (if it will be possible) the output value

---
## PUT and DELETE


```python

@app.delete("/api/cars/{id}", status_code=204)
def remove_car(id: int)->None:
    matches = [car for car in db if car.id == id]
    if matches:
        car = matches[0]
        db.remove(car)
        save_db(db)
    else:
        raise HTTPException(status_code=404, detail=f'No car with id={id}.')

@app.put("/api/cars/{id}", response_model=CarOutput)
def change_car(id: int, new_data: CarInput)-> CarOutput:
    matches = [car for car in db if car.id == id]
    if matches:
        car = matches[0]
        car.fuel = new_data.fuel
        car.transmission =new_data.transmission
        car.size = new_data.size
        car.doors = new_data.doors
        save_db(db)
        return car
    else:
        raise HTTPException(status_code=404, detail=f"No car with id={id}.")


```

## Postman
#postman

You have to add `title` ->
`app=FastAPI(title="Car Sharing")` 
In the Postman create a new workspace
create new environment (*localhost* was called)
create a variable (*basedUrl* was created)
initial value: http://localhost:8000
remember to check this environment 
now button "import" in Postman
from the browser with docs of our FastAPI copy link `/openapi.json` ( it will be `http://localhost:8000/openapi.json`)
in Postman chose *link* and paste this link


