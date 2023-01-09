[[_HTML-W3school]]


---

# HTML links
Links can be any HTML document (text, image, ...)

`<a>` defines a hyperlink
```html
<a href="url"> link text </a>
```

atrybut `target` opens the documnents:
- `_self` (default)in the same window/tab
- `_blank` in a new window or tab
- `_parent` in the parent frame
- `_top` in the ful body of the window

---

## Link to image

To use an image as a link, just put teh `<img>` tag inside the `<a>` tag
```html
<a href="default.asp">
<img src="smiley.gif" alt="HTML tutorial" style="width:42px;height:42px;">
</a>
```

---

## Link to an email address
`mailto:`
```html
<a href="mailto:some@example.com"> Send email </a>

```


## Button as a link   JS
JavaScript allows you to specify what happens at certain events, such as a click of a button:
```html
<button onclick="document.location='default.asp'"> Html </button>


```


---
---

# Link Colors
By default:
- an unvisited link is underlined and blue
- a vistited link is underlined and purple
- an active link is underlined and red

Using CSS you can change the link state colors

```html
<style>
a:link {
  color: green;
  background-color: transparent;
  text-decoration: none;
}

a:visited {
  color: pink;
  background-color: transparent;
  text-decoration: none;
}

a:hover {
  color: red;
  background-color: transparent;
  text-decoration: underline;
}

a:active {
  color: yellow;
  background-color: transparent;
  text-decoration: underline;
}
</style>
```


---
# Bookmark in HTML
Bookmarks can be useful if a web page is very long.

First:
use the `id` attribute
`<h2 id="C4"> Chapter 4 </h2>`

Then, add a link to the bookmark:
`<a href="#C4"> Jump to Chapter 4 </a>`

or on another page:
`<a href="thml.demo.html#C4"> Jump to Chapter 4 </a>`






