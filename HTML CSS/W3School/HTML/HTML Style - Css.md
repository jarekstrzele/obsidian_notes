[[_HTML-W3school]]




---

# HTML Style - CSS

> CSS stands for Cascading Style Sheets

__cascading__ means that a style applied to a parent element will also apply to all also apply to all children elements within the parent 


## Using CSS
CSS - __Inline__ by using the `style` attribute inside HTML elements
`<p style="color:red;">A red paragraph.</p>`


- __Internal__ by using a `<style>` element in the `<head>` section
```html
<!DOCTYPE html>
<html>
<head>
<style>
	body {background-color: powderblue;}
	h1   {color: blue;}
	p    {color: red;}
</style>
</head>
<body>

	<h1>This is a heading</h1>
	<p>This is a paragraph.</p>

</body>
</html>
```


- __External__ by using a `<link>` element to link to an external CSS file
```html
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="styles.css">
</head>
<body>

<h1>This is a heading</h1>
<p>This is a paragraph.</p>

</body>
</html>

```

```css
body {
  background-color: powderblue;
}
h1 {
  color: blue;
}
p {
  color: red;
}
```

---

## CSS Colors, Fonts, Sizes

__text__:
- `color:blue` defines the text color to be used
- `font-family:verdan` defines the font to be used
- `font-size:160%` defines the text size to be used


__Border__
`border: 2px solid powderblue;` defines a border around an HTML element


__CSS Padding__
`padding: 30px;` defines a padding(space) between the text and the border


__CSS Margin__
`margin: 50px` defines a margin(space) outside the border

---

##  Link to External CSS

by URL
`<link rel="stylesheet" href="https://www.w3schools.com/html/styles.css">`

in the local folder
`<link rel="stylesheet" href="/html/styles.css">`

in the same folder
`<link rel="stylesheet" href="styles.css">`

---

`<style>` defines style information for an HTML document
`<link>` defines a link between a document and an external resource








