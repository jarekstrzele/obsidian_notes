[[_ 0 start REST API i python]]



-------

# Struktura projektu
1. `main.py` zwięźle napisane endpointy 
	1. a logika w innym pliku -> do folderu `src`
	2. a modele w innym pliku -> do folderu `models`
2. aby ułatwić importowanie:
	1. w folderze models w pliku `__init__.py` umieszczamy to, co będzie importowane przez `main.py` 
```python
# __init__.py
from .user import User, UserSafe
from .message import Message
```

```python
# main.py
import models

# models.User, models.Message , ....
```

----
Refaktoryzacja c.d.
1. często powtarza się kod obsługi bazy danych, więc w `src` tworzymy `__init__.py` oraz plik `database.py`
2. w pliku `database.py` umieszczamy logikę interakcji z bazą danych (ważna jest dokumentacja!!)
```python
# main.py
# ...
@app.get("/users", response_model=List[models.UserSafe], tags=["users"])
def users_all():
    """Get all users from database"""
    return Database().get_all_users()

#...
```

```python
# database.py

from typing import List, Dict
from pymongo import MongoClient   
from fastapi import HTTPException
from pymongo.errors import ServerSelectionTimeoutError, DuplicateKeyError
import models


class Database:
    def __init__(self) -> None:
        # inicjalizacja klienta
        client = MongoClient(serverSelectionTimeoutMS=5000)
        try:
            client.server_info() # zwraca informacje o serwerze
        except ServerSelectionTimeoutError as e:
            raise HTTPException(status_code=503, detail="Problem with connection to database")
        self.collection = client['data']['users']
    def get_all_users(self) -> List[models.UserSafe]:
        """
            Method for fetching data from mongoDB about all users

        Returns:
            List[models.UserSafe]: Returns list of users in UserSafe model format.
        """
        result = self.collection.find({})
        return list(result)   

# ...

```












