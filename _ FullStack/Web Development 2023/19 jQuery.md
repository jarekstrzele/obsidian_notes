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


# Selecting elements with jQuery








