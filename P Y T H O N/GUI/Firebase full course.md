#python #firebase #hala #youtube 
https://www.youtube.com/watch?v=s-Ga8c3toVY

[[Simple app with FireBase]]

# `pip install pyrebase4`
https://pypi.org/project/Pyrebase4/


## `import pyrebase`

-----------
# Index

1. [[#Authentication]]
2. [[#Storage]]
	1. [[#get the url]]
	2. [[#download]]
	3. [[#reading file]]
3. [[#Database]]
	1. [[#send]]
	2. [[#update]]
	3. [[#delete]]
	4. [[#read data]]
	5. 



-------
you have to add  a desktop app to firebase as a web app (look at Project overview of your FireBase Project (e.g. test))

after registration:
```javascript
// Import the functions you need from the SDKs you need
import { initializeApp } from "firebase/app";
// TODO: Add SDKs for Firebase products that you want to use
// https://firebase.google.com/docs/web/setup#available-libraries

// Your web app's Firebase configuration
const firebaseConfig = {
  apiKey: "AIzaSyBSpLK0ThyXOuOXMgl_oYF0iQ8I7Qlh6oc",
  authDomain: "test-7a2ea.firebaseapp.com",
  databaseURL: "https://test-7a2ea-default-rtdb.firebaseio.com",
  projectId: "test-7a2ea",
  storageBucket: "test-7a2ea.appspot.com",
  messagingSenderId: "455697270541",
  appId: "1:455697270541:web:c625f5c109b77c811b1244"
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);
```

copy `const firebaseConfig` to your python file and keys change to string
```python
firebaseConfig = {
  "apiKey": "AIzaSyBSpLK0ThyXOuOXMgl_oYF0iQ8I7Qlh6oc",
  "authDomain": "test-7a2ea.firebaseapp.com",
  "databaseURL": "https://test-7a2ea-default-rtdb.firebaseio.com",
  "projectId": "test-7a2ea",
  "storageBucket": "test-7a2ea.appspot.com",
  "messagingSenderId": "455697270541",
  "appId": "1:455697270541:web:c625f5c109b77c811b1244"
};

firebase=pyrebase.initialize_app(firebaseConfig)

db = firebase.database()
auth=firebase.auth()
storage=firebase.storage()
```


-------------------
# Authentication
[[#Index]]
It means: mange users
Goto FireBase Project overview > Build and Authentication > Get Started and chose the sign-in method

### login or sign up
```python
import pyrebase
  

firebaseConfig = {
"apiKey": "AIzaSyBSpLK0ThyXOuOXMgl_oYF0iQ8I7Qlh6oc",
"authDomain": "test-7a2ea.firebaseapp.com",
"databaseURL": "https://test-7a2ea-default-rtdb.firebaseio.com",
"projectId": "test-7a2ea",
"storageBucket": "test-7a2ea.appspot.com",
"messagingSenderId": "455697270541",
"appId": "1:455697270541:web:c625f5c109b77c811b1244"
};
  

firebase=pyrebase.initialize_app(firebaseConfig)
# db = firebase.database()
auth=firebase.auth()
# storage=firebase.storage()

#LOGIN
# email=input("Enter email: ")
# password=input("Password: ")
# auth.sign_in_with_email_and_password(email, password)
# print("Ok")
  

#SIgnUP
email=input("Enter email: ")
password=input("Password: ")
confirmpass=input("Confirm password: ")
if password == confirmpass:
	auth.create_user_with_email_and_password(email, password)
	print('sign up')
else:
	print('something wrong')
```

-------
# Storage
[[#index]]
>[!important] storage
>Store and retrieve user-generated files like images, audio, and video without server-side code

I added tree txt files to the project.
Manually create `subfolder` in firebase storage.


```python
import pyrebase
from collections.abc import MutableMapping

firebaseConfig = {
"apiKey": "AIzaSyBSpLK0ThyXOuOXMgl_oYF0iQ8I7Qlh6oc",
"authDomain": "test-7a2ea.firebaseapp.com",
"databaseURL": "https://test-7a2ea-default-rtdb.firebaseio.com",
"projectId": "test-7a2ea",
"storageBucket": "test-7a2ea.appspot.com",
"messagingSenderId": "455697270541",
"appId": "1:455697270541:web:c625f5c109b77c811b1244"
};

firebase=pyrebase.initialize_app(firebaseConfig)
# db = firebase.database()
#auth=firebase.auth()
storage=firebase.storage()


#LOGIN
# email=input("Enter email: ")
# password=input("Password: ")
# auth.sign_in_with_email_and_password(email, password)
# print("Ok")

#SIgnUP
# email=input("Enter email: ")
# password=input("Password: ")
# confirmpass=input("Confirm password: ")
# if password == confirmpass:
# auth.create_user_with_email_and_password(email, password)
# print('sign up')
# else:
# print('something wrong')


# Storage
filename=input("enter the naem of the file you want to upload: ") # which file upload to the storage
cloudfilename=input("Enter the name of the file on the cloud: ") # the name of that file on the storage
storage.child(cloudfilename).put(filename)
print("Suucess")
```

```bash
> enter the naem of the file you want to upload: baczynski_noc.txt
> Enter the name of the file on the cloud: books/poems/poem1.txt
```

`> Enter the name of the file on the cloud: dummy.txt`

### get the url
[[get_url]]

```python
filename=input("enter the naem of the file you want to upload: ") # which file upload to the storage

cloudfilename=input("Enter the name of the file on the cloud: ") # the name of that file on the storage

storage.child(cloudfilename).put(filename)

print(storage.child(cloudfilename).get_url(None))
```

```bash
$ python3 consoleApp_auth_firebase.py 
enter the naem of the file you want to upload: slimak_wiki.txt
Enter the name of the file on the cloud: slimak.txt
https://firebasestorage.googleapis.com/v0/b/test-7a2ea.appspot.com/o/slimak.txt?alt=media
```

### download
```python
cloudfilename=input("Enter the name of the file on the cloud: ") # the name of that file on the storage

storage.child(cloudfilename).download("", "my_poem.txt")
```
`.download(path, new_file_name)`


### reading file
[[urllib]]
```python
# ...
import urllib
# ...

cloudfilename = input("Enter the name of the file you want to download: ")
url=storage.child(cloudfilename).get_url(None)
f=urllib.request.urlopen(url).read()
print(f)
```

----------
# Database
[[#Index]]
[[Simple app with FireBase]]

```python
import pyrebase
import urllib

firebaseConfig = {
"apiKey": "AIzaSyBSpLK0ThyXOuOXMgl_oYF0iQ8I7Qlh6oc",
"authDomain": "test-7a2ea.firebaseapp.com",
"databaseURL": "https://test-7a2ea-default-rtdb.firebaseio.com",
"projectId": "test-7a2ea",
"storageBucket": "test-7a2ea.appspot.com",
"messagingSenderId": "455697270541",
"appId": "1:455697270541:web:c625f5c109b77c811b1244"
};

firebase=pyrebase.initialize_app(firebaseConfig)
db = firebase.database()

data = {'age': 40, 'address':'New York', 'employed': True, 'name':'Joe Dow'}
db.push(data) # add data as a child of the root
```

## send 
```python
########################
# better practice
data = {'age': 40, 'address':'New York', 'employed': True, 'name':'Joe Dow'}
db.child("people").push(data)
# you can also `db.child("people").child("person").push(data)` and so on

data2 = {'age': 22, 'address':'LA', 'employed': False, 'name':'JTom Kris'}
db.child("people").push(data2)
print("ok")
```

##### you can set your own id 
```python
data = {'age': 22, 'address':'LA', 'employed': False, 'name':'JTom Kris'}

db.child("people").child("My_own_id").set(data)
# db.child("people").child("My_own_id").push(data) - FireBase will add its own id
```


## update
```python
# DB

data = {'age': 122, 'address':'Olsztyn', 'employed': True, 'name':'Jan Kowalski'}

# db.child("people").child("id_1").set(data)

# update
db.child("people").child("id_1").update({'name':'Tom Nowak'})
print("ok")
```

### update when you don't know the id
in FireBase DB I have 'people' with objects wit random id genereted by DB

```python
# ...
people = db.child("people").get() # get all objects in the people object
for person in people.each():
	print(person.key())
	print(person.val())

```

```bash
-NRXDFT-a1_0WWdUM3UX
{'address': 'New York', 'age': 40, 'employed': True, 'name': 'Joe Dow'}
-NRXE17apKVfCfb-68hI
{'address': 'LA', 'age': 22, 'employed': False, 'name': 'JTom Kris'}

```

```python
people = db.child("people").get() # get all objects in the people object

for person in people.each():
	if person.val()['name'] == 'Joe Dow':
	db.child("people").child(person.key()).update({'name':'Now Osoba AR-54'})
```

----------
## delete
[[#Index]]

Added to firebase
person
	address:"London"
	age:34
	name:"Mary"

and now I will remove the age attribute of that person
```python 
# delete an attribute
db.child("people").child("person").child("age").remove()

# remove a person
db.child("people").child("person").remove()
```

### when you don't know the id
the same logic [[#update when you don't know the id]]
```python
people=db.child("people").get()

for person in people:
	if person.val()['name'] =="Now Osoba AR-54":
			db.child("people").child(person.key()).child("age").remove()
```


----------
# read data
[[#Index]]
`people=db.child("people").get()`

```python
people=db.child("people").child("-NRXDFT-a1_0WWdUM3UX").get()

print(people.val())

# OrderedDict([('address', 'New York'), ('employed', True), ('name', 'Now Osoba AR-54')])
```


### more sofisticated way (conditions)
send data
```python
data = {
'obywatel1': {'age': 12, 'address':'Różnowo', 'employed': False, 'name':'Zosia'}

, 'obywatel2': {'age': 22, 'address':'Różnowo', 'employed': True, 'name':'Genowefa'}

, 'obywatel3': {'age': 37, 'address':'Olsztyn', 'employed': True, 'name':'Artur'}

, 'obywatel4': {'age': 98, 'address':'Olsztyn', 'employed': False, 'name':'Boromir'}

}

db.child("polacy").set(data)
```

**you have to index columns** -> firebase rules and add indexes:
`".indexOn": ["name", "address", "employed", "age" ]`
```
{
  "rules": {
    ".read": "now < 1680300000000",  // 2023-4-1
    ".write": "now < 1680300000000",  // 2023-4-1
      "polacy":{
        ".indexOn": ["name", "address", "employed", "age" ]
      }
  }
}
```
and publish it


and read
```python
people=db.child("polacy").order_by_child("name").equal_to("Zosia").get()

print(people.val()) # OrderedDict([('obywatel1', {'address': 'Różnowo', 'age': 12, 'employed': False, 'name': 'Zosia'})])

for person in people:
	print(person.val())
#{'address': 'Różnowo', 'age': 12, 'employed': False, 'name': 'Zosia'}


# ADDRESSES
for person in people:
	print(person.val()['address']) # Różnowo, because Zosia lives in Różnowo

# or with map
find_addresses = lambda person: person.val()['address']
addresses = list(map(find_addresses, people)) # map returns generator (it is lazy), so you have to convert the generator into a list
print(addresses)
# ['Różnowo']

# all data of people living in Różnowo
people=db.child("polacy").order_by_child("address").equal_to("Różnowo").get()

for person in people.each():
	print(person.val())

# an age of people living in Rożnowo
for person in people.each():
	print(person.val()['age'])



```

```python

# people between 22 and 50
people=db.child("polacy").order_by_child("age").start_at(22).end_at(50).get()
for person in people.each():
	print(person.val())

# {'address': 'Różnowo', 'age': 22, 'employed': True, 'name': 'Genowefa'}
# {'address': 'Olsztyn', 'age': 37, 'employed': True, 'name': 'Artur'}


people=db.child("polacy").order_by_child("age").start_at(22).end_at(50).limit_to_first(1).get()
for person in people.each():
	print(person.val())
# {'address': 'Różnowo', 'age': 22, 'employed': True, 'name': 'Genowefa'}



people=db.child("polacy").order_by_child("age").start_at(22).end_at(50).limit_to_last(2).get()
for person in people.each():
	print(person.val())
# {'address': 'Różnowo', 'age': 22, 'employed': True, 'name': 'Genowefa'}
# {'address': 'Olsztyn', 'age': 37, 'employed': True, 'name': 'Artur'}
```






