[[DOM]]
[[JavaScript]]

---
[[jQuery Events]]
[[jQuery Project]]

---
# jQuery
- is a JS library
- is a large single .js file that has many pre-built methods and objects that simplify your workflow
- 
simplify interactions with the DOM and making HTTP requests (AJAX)


## linking
1. Link a CDN hosted file
2. download the .js file from jQuery's official website

than use `<script>` tags in your HTML

example:
- jQuery: `var divs = $('div')`  vs    javascript: `var divs = document.querySelectorAll('div')` 
- jQuery: `$(el).css('border-width', '20px');`  vs    javascript: `el.style.borderWidth = '20px';`
- jQuery: `$(document).ready(function(){ //code}`    vs javascript: `function ready(fn){ id (document.readyState != 'loading') {fn();} else { document.addEventListener('DOMContentLoaded', fn)}`

---

# jQuery basics
to link:
https://releases.jquery.com


## Change styles
```javascript
var x= $('h1');
x.css('color', 'red');
x.css('background', 'blue');

var newCSS = {
	'color': 'white',
	'background': 'blue',
	'border': 'red'
}
x.css(newCSS)
// {color: "red", background: "blue"}


```

```js
var listItems = $('li');

// to change all items in the list
listItems.css('color', 'blue');

// to change only the first one
listItems.eq(0).css('color', 'orange');

// to change obly the last one
listItems.eq(-1).css('color', 'orange');

```


## grabbing text
```js
$('h1').text() // -> content of h1
$('h1').text("new text in the h1")

$('h1').html("New <em> em text   </em>")
```

## attributes  and values
Change type 'submit' for 'checkbox'
```js
$("input").eq(1).attr("type", "checkbox");
$("input").eq(1).val("New value");
```


## classes
`$('h1').addClass('turnRed');`
`$('h1').removeClass('turnRed');`


`$('h1').toggleClass('turnRed');`
but if you use this command again, this element return to its previous state





