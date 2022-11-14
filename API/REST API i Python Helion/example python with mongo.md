

# example python with mongo
#python #mongodb 

```python
from pymongo import MongoClient 
from bson.objectid import ObjectId # aby móc używać id


client = MongoClient(serverSelectionTimeoutMS=5000) # po 5s braku połączenia wyłącza się
test_collection = client['config']['test1'] # baza danych 'config' kolekcja 'test1'

def create_one():
    test_dict = {
    "some_key1": "value1",
    "some_key2": "value2",
    "some_key3": "value3"
    }
    test_collection.insert_one(test_dict)

def list_all():
    test_collection = client['config']['test1']
    res = test_collection.find({})
    for item in res:
        print(item)

def delete_one(id: str):

    test_collection = client['config']['test1']
    res = test_collection.delete_one({'_id': ObjectId(id)})
    print(res.deleted_count)



list_all()
print("-------")
# create_one()
delete_one('62cc5bdfad5a28c1c918fb97')
print("-------")
list_all()
```

