[[0- Intro functional programming (beginner udemy)]]

---

# Currying

>__Higher-Order Function__ is a function that either takes a function as an input parameter and or returns	 a function

>__Closure__ a function that can access and use variables that are not directly passed into the function because of the placement of the function relative to the variables



We have a simple example:
```js
function greet(greeting, name){
  return `${greeting} ${name}`;
}

console.log(greet('Good Morning', 'Jarek'));
```

We want to do the same with an array
```
const friends = ['Nate', 'Jim', 'Scott', 'Dean'];
const friendsGreeting = friends.map(greet);
```
We can't use the map function,  because our function take two arguments:
`console.log(friendsGreeting)` =>`["Nate 0", "Jim 1", "Scott 2", "Dean 3"]`


```js
function greet(greeting){
 // return `${greeting} ${name}`;
  return function(name){
    return `${greeting} ${name}`;
  }
}
const friends = ['Nate', 'Jim', 'Scott', 'Dean'];

const friendsGreeting = friends.map(greet('Good Morining'));
console.log(friendsGreeting);

```
=>
`["Good Morining Nate", "Good Morining Jim", "Good Morining Scott", "Good Morining Dean"]`























