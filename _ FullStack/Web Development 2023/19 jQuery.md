#jquery 
[[_ FullStack/Web Development 2023/_ 0 start]]

John Resig  invented a library jQuery
- `document.querySelector("h1)"` ---> 
	- `jQuery("h1")` ----> 
		- `$("h1")`

# Incorporate `jQuery` into 
`https://jquery.com/download/` CDN from Google 
`https://developers.google.com/speed/libraries?hl=pl#jquery`

> make `index.html` and and just before `</body>` this code `<script src="index.js " charset="utf-8"> </script>`
> in `index.js` write `alert("Work!")` to verify that our `html` and `js` are connected

now my `index.js` only contains `$("h1").css("color", "red")` 
and in my `index.html`:
```html
<!-- ....

-->

<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.7.1/jquery.min.js"></script>

        <script src="index.js " charset="utf-8"> </script>

    </body>

</html>

```

if you place jQuery in the `<head>`, you have to add to your `.js`
```js
$(document).ready(

    $("h1").css("color", "blue")

)
```
if `document` have been read, you can start `jQuery` library

you can use `mini-jquery`
you can minify your `js` or `css` code:  https://www.minifier.org/


# Select and Manipulate elements with jQuery

## select
`$("h1")` means select all `h1` in your web page

## Manipulatint the css style
`$("button").css("color")` this is the **getter** (give me a value of the attribute `color`)
`$("button").css("color", "blue")` this is the **setter** (set the attribute `color` to "blue")

to **separate** styles from the js code you can do:
- add `style.css` to your project
```css
.big-title{
    font-size: 32;
    color: cadetblue;
    font-family: 'Franklin Gothic Medium';
}
```
- add to `index.html` ` <link rel="stylesheet" href="style.css">`
- add to `index.js` 
`$("h1").addClass("bit-title")`

```css
.big-title{
    font-size: 5rem;
    color: cadetblue;
    font-family: 'Franklin Gothic Medium';
}
.margin-50{
    margin:50px;
}
```

add two classes 
```js
$("h1").addClass("big-title margin-50")
```


in the console you can check other methods:
`$("h1").removeClass("margin-50")` remove the klas
`$("h1").hasClass("margin-50")`



## Manipulating text
`.text()` zmiana tekstu, nie rozpoznaje znaczników html
`.html()` zmiana tekstu, rozpoznaje znaczniki htlm

```js
$("h1").text("Nowy tytuł")
$("button").html("<em> Cliiiiick him </em>")
```


# Manipulating attributes
> select all `img` and return the value of `src`
> `$(img).attr('src')`

>select all `a` and set `href` to `interia.pl` 
>`$(a).attr('href', 'interia.pl')`


`class` is also an attribute

```js
$("h1").addClass("big-title margin-50")
$("h1").text("Nowy tytuł")

$("button").html("<em> Cliiiiick him </em>")

$("a").attr("href", "https://www.interia.pl")
```

```html
<!-- ... -->
  <link rel="stylesheet" href="style.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.7.1/jquery.min.js"></script>
</head>
<body>
  <h1> My first jQuery app</h1>
  <button>Click me</button>
  <button>Click me</button>
  <button>Click me</button>
  <button>Click me</button>
  <a href="https://www.google.com">To nie jest strona google.pl</a>
  <script src="index.js " charset="utf-8"> </script>
</body>

```

# Add Event Listener
```js
$("h1").click(()=>{
    $("h1").css("color", "red")
})
```

```js
 $("button").click(()=>{
    $("h1").css("color", "purple")
 })
```



```html
<input type=text value="" />
```

```js
// show in the console the key that have been pressed
$("input").keypress((event)=>console.log(event.key))
```

```js
$("input").keypress((event)=>{

    $("h1").text(event.key)

 })
```









