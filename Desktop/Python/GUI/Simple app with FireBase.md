#firebase #databases  #python 

https://www.youtube.com/watch?v=_zm1uEUregI
https://www.youtube.com/watch?v=rKuGCQda_Qo
https://www.youtube.com/watch?v=8IWalfRUk1M


# Dependences
- for requests  to db: `pip intall requests`
- for firebase: `pip install python-firebase`

-  for firebase authetication:  `pip install pyrebase4`
https://pypi.org/project/Pyrebase4/


# App with post (send data)
```python
from firebase import firebase
  

firebase = firebase.FirebaseApplication("https://test-7a2ea-default-rtdb.firebaseio.com/", None) # drugi argument odpowiada za autentykację, tutaj jest brak
# data = {
# 'Name': 'Tom Jerry'
# , 'Email': 'tom@jerry.com'
# , 'Phone': 222333444
# }

data = {
'Name': 'Wiedźmin'
, 'Email': 'wiesiek@saplw.pl'
, 'Phone': 111222333
}

result = firebase.post('/pythonDB_text/Customer', data)
print(result)
```


# App with put (change data)
```python
from firebase import firebase

firebase = firebase.FirebaseApplication("https://test-7a2ea-default-rtdb.firebaseio.com/", None)
# data = {
# 'Name': 'Tom Jerry'
# , 'Email': 'tom@jerry.com'
# , 'Phone': 222333444
# }
 

# data = {
# 'Name': 'Wiedźmin'
# , 'Email': 'wiesiek@saplw.pl'
# , 'Phone': 111222333

# }
# result = firebase.post('/pythonDB_text/Customer', data)

result = firebase.put('/pythonDB_text/Customer/-NROJbrYlDozNg8LEtn4', 'Name', 'Boby')

print(result)
```


# App with get (get data)
```python
from firebase import firebase


firebase = firebase.FirebaseApplication("https://test-7a2ea-default-rtdb.firebaseio.com/", None)

result = firebase.get('/pythonDB_text/Customer/', '')
print(result)


```

# App with del (delete data)













