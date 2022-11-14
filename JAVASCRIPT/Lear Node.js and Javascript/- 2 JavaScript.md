#javascript 

[[_ Node and JavaScript]]

---

# JavaScript


## Output JavaScript to the screen
```html

<!-- FIRST WAY -->
<script>
	document.getElementById("demo").innerHTML = " New text"
</script>

<!-- SECOND WAY -->
<script>
	document.write("I used write method of the dicument object")
</script>

<!-- THIRD WAY -->
<script>
	window.alert("Yes it is an alert ")
</script>

<!-- FOURTH WAY -->
<script>
	console.log("This is a console log")
</script>


```
```javascript

for(start; condition; (de)incrementation){

}

while (condition){ 

}
```

----
# ARRAYS
`var name_arr = ["some", true, 100 ]`

`name_arr[2]`

`var new_arr = [10,20, ["a", "b"]]`
`new_arr[2][1]`


----
# Object
A Python dictionary is like a Javascript object.

```javascript
var person = {
	firstName: "John",
	
}
console.log(person.firstName)

```

----
# Functions
```javascript
function name(args){

	return ;
}

name()
```
----
# Box

## prompt
```javascript
var yourName = prompt("Hello there, please enter your name: ");

```

----
# Random Numbers
#javascript/number
`Math.random()` ->
	0.7827510213047553
	0.4698200385127118
	...
`Math.Floor(Math.random() * 10)` 0-9
`Math.Floor(Math.random() * 10) + 1` 1-10


----
# FORM
#javascript/form
```javascript
function hello(){
  var firstName = document.getElementById('name').value;
  document.getElementById("output").innerHTML = firstName;
}

```

```html
<!DOCTYPE html>
<html lang="en" dir="ltr">
  <head>
    <meta charset="utf-8">
    <script src="myscript.js"> </script>


    <title> My test page</title>
  </head>


  <body>
    <center>
    <h1> FORM </h1>
    </center>

    <p> Hello enter your name </p>
    <input id="name">
    <button type="button" onclick="hello()"> Submit </button>
    <br><br>
    <p id="output"> </p>


  </body>
</html>
```

----

`isNaN(somthing)`
`isNaN(10)` -> false
`isNaN("to")` -> true











