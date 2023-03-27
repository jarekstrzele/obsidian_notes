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
Goto FireBae Project overview > Build and Authentication > Get Started and chose the sign-in method

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

########################
# better practice
data = {'age': 40, 'address':'New York', 'employed': True, 'name':'Joe Dow'}
db.child("people").push(data)
# you can also `db.child("people").child("person").push(data)` and so on
```










