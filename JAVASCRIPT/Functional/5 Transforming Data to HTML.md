[[0- Intro functional programming (beginner udemy)]]

[[5 - HTML and CSS]]

[[5 Generating HTML and CSS]]

---
# Transformin Data to HTML
`<script src="https://cdn.rawgit.com/knowthen/d90da7fbbcc3222252d2845eef2adc38/raw/6099003c3102daf281681cd92b7158477a1bc5f4/hyperscript-browser.js"></script>`
from:
```javascript
const MEALS = [
	{description: 'Breakfast', calories: 460},
	{ ....} ...

]
```
to
```html
...
<table>
 <thead>
	 <tr>
		 <th> Meal </th>
		 <th>Calories</th>
	</tr>
</thead>
<tbody>
	<tr>
		<td> Breakfast </td>
		<td> 460 </td>
		....

</tbody>
```

Build several small functions and combine them together as appropriate

---
our html
the html

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
  <link rel="stylesheet" href="https://unpkg.com/tachyons@4.12.0/css/tachyons.min.css"/>

  
  </head>
<body class="sans-serif bg-white pa3">
  <table class="mw5 center w-100 collapse">
    <thead >
        <tr>
          <th class="pa2 tl"> Meal </th>
          <th class="pa2 tr"> Calories </th>
      </tr>
    </thead>
    
    <tbody>
        <tr class="stripe-dark">
          <td class="pa2"> Breakfast </td>
          <td class="pa2 tr"> 460 </td>
        <tr>
          
           <tr class="stripe-light">
          <td class="pa2"> Snack </td>
          <td class="pa2 tr"> 180 </td>
        <tr>
          
           <tr class="stripe-dark">
          <td class="pa2"> Lunch </td>
          <td class="pa2 tr"> 600 </td>
        <tr>
    </tbody>
  </table>
  

</body>
</html>
```

we have to generate it using JavaScript

---
## SINGLE RESPONSIBILITY PRINCIPLE
#single_responsibility_principle


```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
<script src="https://cdn.rawgit.com/knowthen/d90da7fbbcc3222252d2845eef2adc38/raw/6099003c3102daf281681cd92b7158477a1bc5f4/hyperscript-browser.js"></script>
  <title></title>
 
</head>
<body>
  body
  <div id="app">
  </div>
  
</body>
</html>
```

>![[SINGLE RESPONSIBILITY PRINCIPLE]]
> **Each Function Does 1 Thing**

1. A function that creates a cell in a table
2. A function to create a row in a table (`thead>tr>th` but `tbody>tr>td`):
	1. mealRow()
	2. headerRow()
	3. totalRow() (w html na końcu ma być *total: 1240*)
3. mealBody() to `<tbody>` and mealHeader() to `<thead>`
4. mealsTabel to `<table>`

### cell function
`<td>` or `<th>` + `class attribute` + content 

`tag({atrr1: "v1", attr2:"v2"}, "hello");`
`<tag attr1="v1" attr2="v2> hello </tag>"`
```javascript
const MEALS = [
  {description: "Breakfast", calories: 460},
  {description: "Snack", calories: 180},
  {description: "Lunch", calories: 600}
]

const { td, th } = tags;


function cell(tag, className, value){
  return tag({className: className}, value);
}

const node = document.getElementById('app');
const view = cell(td, 'pa2', 'Lunch');
node.appendChild(view);
```
```javascript
const MEALS = [
  {description: "Breakfast", calories: 460},
  {description: "Snack", calories: 180},
  {description: "Lunch", calories: 600}
]

const { td, th } = tags;

function cell(tag, className, value){
  return tag({className}, value);
}

function mealRow(className, meal){
  return tag({className}, [
    cell(td, 'pa2', meal.description),
    cell(td, 'pa2 tr', meal.calories),
  ]
});

const node = document.getElementById('app');
const view = mealRow('stripe-dark', {description: "Lunch", calories:500});
  
node.appendChild(view);



```

