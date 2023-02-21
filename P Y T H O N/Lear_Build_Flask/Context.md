
[[_ Intro Scalable Web Applications with Python, Flask and SQLAlchemy]]

[[P Y T H O N/Lear_Build_Flask/Git]]


---
# Section 7 Context
## There are two contexts:
- ==request context== - is created and removed by Flask  
	- __request object__
		- it captures the details of the request, which can be futher used in other function

![[flask_context.excalidraw|600]]

When a user submits request, Flask creates a few other variables or context -> for example: __session object__ 

A session starts when a user logs into the server and ends when the user logs out
session object: starts :log-in ends: log-out, __is a 
python dictionary__,
`app.config.update(secrect_key="fsfweewfr")` -- to secure  




```py
from flask import session

@app.route('/session')
def session_data():
      if 'name' not in session:session[,name,]='harry'
      
      return render_template('session.html'session=session,name=session['name'])  
```


- ==application context==:
	- global variable "g"
	- current_app
__request decorators__
	`@app.before_request` executes a piece of code or function before each and every get request
	`@app.before_first_request` executes afunction or a piece of code only before the very first request
	`@app.after_request` executes a piece of code after that request is submitted, but only if exceptions occur
	`@app.teardown_request` executes a function on call after every request, even if exceptions occur

_example_
- you may wish to find out if a user is already logged into our application or you may want to establish a database collection before you serve any user requests
	```
		@app.before_request:
		def check_login_status():
		   do sth ...
	```

application connext  
global variable "g"  
current_app  
```py
from flask import g
# request decorators:
@app.before_request
# e.g.
def check_login_status():.....
def connet_to_database():.... 

@app.before_first_request
@app.after_request
@app.teardown_request  
```
  

```py
@app.before_request
def some_fnc():
    g.string = '<br> THis code run before any request'



# BASIC ROUTE
@app.route('/index')
@app.route('/')
def hello_flask():
    return "Hellow Flask! <br>" + g.string

```












