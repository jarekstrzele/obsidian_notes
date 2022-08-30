[[0- Intro functional programming (beginner udemy)]]
[[Reduce]]


# MODIFY ARRAYS IN IMMUTABLE WAY 

> use **...spread operator**  
#javascript/spread


```js
const tabObjs = [
{ prop1:"dkdkd", prop2: 123},   
{ prop1:"xxxxkd", prop2: 3}
];  

const obj = { prop1:"dkfwfwedkd", prop2: 12231313};  

const newTab = [...tabObjs, obj ];  
console.log(newTab)  
```

**UPDATING array**  
MAP FUNCTION (działa)  
```js
const tabObjs = [
   { id:1, prop1:"one", prop2: 111},   
   { id:2, prop1:"two", prop2: 222}
];  

const obj = { id: 3, prop1:"three", prop2: 333};

const obj2_update = {...obj, prop1:"nonnn"};  

console.log(obj2_update);  

console.log('-------------------')  

const newTab = [ ...tabObjs, obj2_update];  

console.log(newTab);  

console.log('-------------------')  

function foo(o){  
	if(o.id === 2){  
		return {  
	      ...o, prop1:"twotwotwotwo"  
    }  
  }  
  return o;  
};  

const nn = newTab.map(foo);  
console.log(nn);
```


## REMOVE item from array with immutable way  

 **FILTER to remove item from the array**  
#javascript/filter
```js
array_name.filter(function() {    
// item rests if this funct return true else item is excluded 
      return meal.id !== 1;
// meal = 1 will be exluded});  
```

zadania: rozwiązanie:  
 [https://jsbin.com/vutatg/1/edit?js,console](https://jsbin.com/vutatg/1/edit?js,console "https://jsbin.com/vutatg/1/edit?js,console")   
 
```js
const friends = ['jan', 'tom'];   
const updateFriends = [...friends, 'franek'];  
console.log(friends);  
console.log(updateFriends);  

const friendNameLength = updateFriends.map(function(friend) {  
   return friend.length;  
});  

console.log(friendNameLength);  

const shorterNamedFriends = updateFriends.filter(function(friend){  
  return friend.length !== 6; // NIE DZIAŁA  
}  

console.log(shorterNamedFriends);  
```



