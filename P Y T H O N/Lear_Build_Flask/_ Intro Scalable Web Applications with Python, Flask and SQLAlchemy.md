

# Intro Scalale Web Applications
#udemy
#python  #flask  #python/sqlalchemy  #web_app
#Hara_Gopal 


[[routing in flask]]
[[Jinja 2]]
[[PostgreSQL]]
[[P Y T H O N/Lear_Build_Flask/Git]]
[[P Y T H O N/Lear_Build_Flask/Context]]
[[scalable architecture]]
[[Databases models]]
[[Bootstrap and flask]]

[[Working with Forms]]
[[PERFORMING CRUD OPERATIONS USiNG FORM]]
[[ERROR HANDLING IN FLASK]]
[[DEPLOYING FLASK APPLICATIONS TO HEROKU]]

---

## Virtual environments
[[0 python ogólne]]


`pip3 install virtualenv  `

`mkdir flaskprojectcd flaskprojectvirtualenv flaskenv  `

`source flaskenv/bin/activatedecativate  

to see all installed dependecies
`pip3 freeze`

__PYCHARM__

---

## FLASH intro
  folder **templates** (html files)
  folder **static** (css, js, images) 
  run.py
 
==run.py:==
```py
from flask import Flask
  app = Flask(__name__)
       
  @app.route('/')
  def hello_world():
    
    return ' Hello World!!!!'

  if name == 'main':
    app.run(debug=True)  

```   

`python3 run.py`


---

## HTTP intro

#html 
`hyper text transfer protocol  HTTP`

![[request_response.excalidraw|700]]

  GET request   |    response
--------------- | ---------------- 
 1.request or <br> start-lin | 1. status-lin
 2.header | 2. header
 3.body | 3. body

**GET REQUEST**      [www.abc.xom/?greeting=hello](http://www.abc.xom/?greeting=hello "http://www.abc.xom/?greeting=hello")  <-- params   
1. request-line: `GET/<path to resource>/HTTP 1.1.`
2. header: ----
3. body: .....

__RESPONSE__ has structure:  
- status-line: HTTP1.0 200 OK  
- header  
-  body 

---
example:

w pasku przeglądarki: `localhost:500` <- to jest __GET Request__

to, co wyświetla przeglądarka ("Hello flask!") <- to jest __Response


---

## Response Status Code:
- 2XX - OK
- 3XX - redirected
- 4XX client errors
- 5XX server errors

---

## POST reguest

GET | POST
----| ----
get data | post data
www.abc.com/?greeting=hello | parameters in the body
has max length | no max length
can be cached or bookmarked | not cached or bookmarked
don't change server state | post, update, delete data




























