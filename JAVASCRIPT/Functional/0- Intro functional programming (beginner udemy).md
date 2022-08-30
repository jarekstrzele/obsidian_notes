[[Modify arrays in immutable way]]
[[Types of functions]]
[[Reduce]]
[[Currying]]

[[5 - HTML and CSS]]
[[6 - functional concepts]]
[[7 - First Functional App From Scratch (Simple Counter)]]
[[8 - Calory Counting App]]


---
## To be a much better functional programmer `Elm`
## https://elm-lang.org

---

# Intro JS functional

#udemy   #functional_programming

James Moore  
#James_Moore
  
## Key Concepts  
-   data      
-   lists of data      
-   data transformations      

Each app has the same skeleton.   
slack  -> if you have some problems  

---
## Spaced repetition
https://www.knowthen.com/spaced-repetition/

spaced repetition - a way to learn  
[[spaced repetition]]
#spaced_repetition
a wiki link [spaced repetition](https://en.wikipedia.org/wiki/Spaced_repetition)


---

 [jsbin.com](http://jsbin.com "http://jsbin.com/")   

## PRIMITIVE DATA  
- string
- number  
- boolean  
- undefined  
  

## COMPLEX  
*object*
```js
const meat ={  
      description : 'Breakfast',  
      calories: 180,  
      date: new Date(2020,1,1  
}
```

*Dates*  
`new Date(2020,0,1)`

*Arrays*
[]  

---
## I M M U T A B L E    D A T A  
data that never changes  
e.g.   
	string   
      `const PI =3.14;`  


In JavaScript immutable data is not supported well  

`const PI = 3.14; // is immutable  `
`const ob = { aa:"xx", bb:123}; // is a constant but you can change value of aa, bb `
>**state** is the thing your program remembers  

every apps have states  
so  
how can you use immutable data in our programms?  

- - - - - - - -  

## SPREAD OPERATOR
#javascript/spread 

is on **the right side of the equel sign**  
```js
const meal = {   
      p1: "xxX"  
}  

const meal2 = {   
      p1: meal.p1,  
      p2: "new"  

}
// better way :
// essentially, the properties within the original object   
// are injected into the new object  

const meal2 = {   
      ...meal,  
      p2: "new"  
}  

``` 

## D E S T R U C T U R I N G  
```js
const a = objectName.prop1;
const b = objectName.prop2;
```

better way
```js
const {prop1, prop2} = objectName;  
```
You have to use the same property names:  
```js
const obj = {   
  prop1: "first",  
  prop2:"second",  
  prop3:3  
};  
// const a = obj.prop1;  
// const b = obj.prop2;  
const {prop1, prop3} = obj;  
console.log(prop1, prop3);  
```
  

## REST operator
#javascript/rest
**is on the left side of the equal sign**  
```js
const obj = {   
  prop1: "first",  
  prop2:"second",  
  prop3:3  
};  

const {prop3, ...newObj} = obj;
console.log(newObj);  

>[object Object] {  
  prop1: "first",  
  prop2: "second"  
}

//rest   
const {prop2, ...newObj} = obj;  
console.log(newObj);  

> [object Object] {  
  prop1: "first",  
  prop3: 3  
}

```

[[Modify arrays in immutable way]]
[[Reduce]]