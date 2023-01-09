[[_CSS wstęp]]



---
# CSS Background
to add background effects for elements

## background-color
`background-color` property specifies the background  color  of an element

You can set the  _background-color_ for any HTML elements
```css
h1 {
  background-color: green;
}

div {
  background-color: lightblue;
}

p {
  background-color: yellow;
}
```

`opacity` (0-1) specifies the transparency of an element
```css
div {
  background-color: green;
  opacity: 0.3;
}

div {
  background: rgba(0, 128, 0, 0.3) /* Green background with 30% opacity */
}
```

---

## background-image
to set the background image for any elements

```css
body {
  background-image: url("paper.gif");
}

p {
  background-image: url("paper.gif");
}


```

---
## background repeat
to set how a background image will be repeated
`background-image: url(some.jpg)` 
`background-repeat: repeat-x;` The image will be repeated horizontally 
`repeat-y` - vertically

by default vertically and horizintally


`background-repeat: no-repeat;`


```css
body {
  background-image: url("img_tree.png");
  background-repeat: no-repeat;
  background-position: right top;
}
```










