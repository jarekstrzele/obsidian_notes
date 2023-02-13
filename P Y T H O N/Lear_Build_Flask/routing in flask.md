[[_ Intro Scalable Web Applications with Python, Flask and SQLAlchemy]]

---
# Routing in flask
[[Jinja 2]]




## Understanding QUERY STRINGS

>**query string**
>  allow users to pass their own values

`http://www.abc.com/?greeting=hello` 
`?greeting=hello` is a query string
  
*REQUEST OBJECT*:  
- context variable  
- holds the GET request details (sends by the user)  
- is a python dictionary   
- [http://127.0.0.1:5000/new/?greeting=bonjour](http://127.0.0.1:5000/new/?greeting=bonjour "http://127.0.0.1:5000/new/?greeting=bonjour"query_val = request.args.get('greeting')  

```py

@app.route('/new/')
def query_sting(greeting="hello"):
    query_val=request.args.get('greeting', greeting_default)
    return '<h1> the greeting is : {0}'.format(query_val)
```

in the browser:
`localhost:5000/new/?greeting=jarek`
`query_val` = 'jarek'
`(greeting="hello")` is a default value




__string__ more sofisticated
```py  
# no query string
@app.route('/user')
@app.route('/user/<name>') 
#<name> is a variable
def no_query_strings(name='mina'):
    return '<h1> hellO there ! {}<h1>'.format(name)  
```
in the browser:
`localhost:5000/user/jarek`
->
`hellO ther! jarek'




**numbers**
```py
@app.route('/add/<int:num>')
def working_with_numbers(num):
      return '<h1> the number you picked is:  : {} ' + num + '<h1>'  

# numbers
@app.route('/add/<int:n1>/<int:n2>')
def adding_integers(n1, n2):
     return '<h1> the sum is : {} '.format(n1+n2) + '</h1>'}  

```  

also
`<float: num1>`

---



## RENDERING HTML TEMPLATES  
```py
form flask import render_template  

#USING TEMPLATES
@app.route('/temp')
def using_templates():
       return render_template('hello.html')  

```

`hello.htm` has to be in the `templates` folder!!









