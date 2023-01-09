[[_HTML-W3school]]
#w3school 

CSS color [[Color html]]


---

# CSS Wstęp

CSS describes how HTML elements should be displayed.
Cascading Style Sheets

## Syntax

	SELECTOR {property: value; property: value}

The selector points to the HTML element you want to style.
```css
p {
	color:red;
	text-align: center;
}
```

p - selector
color - property
red - value

## Selectors
We can divide CSS selectors into five categories:
- simple selectors (select elements based on name, id class),
- combinator selectors (select elements based on a specific relationship betweem them)
- pseudo-class selectors (select elements based on a cerain state)
- pseudo-elements selectors (select and style a parto of an element)
- attribute selectors (select elements based on an attribute value)


### the CSS element selector
__by name__
```css
p{
	text-align: center;
	color: red;
}
```

__by id__
```css
#paral {
	text-align: center;
	color: red;
}
```

>an id name cannot start with a number!


__by class__
```css
.center {
 ...
}
```

inly `<p>` elements with class="center" will be red and center-aligned:
```css
p.center{
	text-align: center;
	color: red;
}
```

to refer to more than one class
`<p class="center large"> THis paragraph refers to two classes. </p>`


>an class name cannot start with a number!





__by *  - universl selector__
```css
* {
  text-align: center;
 color: blue;
}
```

grouping
```css
h1, h2, p {
 ...

}
```


---

## How to add CSS
- external CSS
- Internal CSS
- Inline CSS

### external
`<link rel="stylecheet" href="mystyle.css">`

### internal
```html
<style>
body {
	background-color: linen;
}

</style>

```

### inline
`<h1 style="color:blue; text-align:center" > ... </h1>`

















