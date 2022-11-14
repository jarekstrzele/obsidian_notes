#javascript 

[[DOM]]


---

# JavaScript
[[#f u n c t i o n]]
[[#a r r a y]]
[[#o b j e c t]]

---

`===`       equality  
`!==`      not equality  

`for ... in ...`       loops through a JS object
`for ... of ...`       used with arrays

---

## f u n c t i o n  
```js 
funtion name(params){  
     // body  
}  
```
func_name()   - execute  
func_name      - call  


**a variable defined in the function => its scope is i limited to that function**  

---

## a r r a y
iteration  
`for _ of _ {}     `
```js
for(letter of arr) {  
           console.log(letter)  
}  
```
to execute a function on each element of array:  
#javascript/forEach
`array.forEach(function_name)  `
`my_arr.forEach( alert )  `             

to remove elem from the array
```js
var index = arr.indexOf(elemToremove)  
arr.splice(index,1) //
```

---

## o b j e c t
`my_obj = { key1: "value 1", key2:"value 2", ...};`
(any specific order of object elements)

keys are without `" "`, but:
`my_obj["key1"]` -> `"value 1"`

```js
var my_obj = {a:123, b:[1,2,3,4], c:{inside:[10,20,30]}}
console.dir(my_obj)

{
    "a": 123,
    "b": [
        1,
        2,
        3,
        4
    ],
    "c": {
        "inside": [
            10,
            20,
            30
        ]
    }
}

```


```js
var simple = {
	prop: "Hello, I am prop",
	myMethod: function(){
		console.log("Tue myMethod was called  " + this.prop);
	}
};

simple.prop;
simple.myMethod();


```
























