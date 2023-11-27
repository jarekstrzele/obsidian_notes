[[_ 0 Django 4]]


# HTML Django4
#html 

==HyperText Markup Language==:
- Markup Language just means it includes metadata for annotating the document (webpage) which is visually distinguishable from how the user sees the document ( `<title> Title in Tab </title>` defining a title in the tab)
- Hypertext refers to links

## HTML tags - basics
https://www.w3schools.com/html/default.asp
https://developer.mozilla.org/en-US/docs/Web/HTML

`index.html`
- heading `<h1> ... </h1>` (h2, h3, h4, h5, h6)
- emphasis `some text <em> some tekst </em>`
- paragraph `<p> some text </p>`
- `<head> ... </head>` metadata of a web page
- `<body> ... </body>` content of a web page
- 

## HTML list
- ordered list
```html
<ul>
	<li> ... </li>
	<li> ... </li>
</ul>
```
- unorderlist
```html
<ol>
	<li> ... </li>
	<li> ... </li>
</ol>
```


## Divs and Spans
```html
<div> 
		... 
</div>
```
- divisions in out HTML
- divide your web page into different sections

`<span> ... </span>`
like `div` but it is used to create inline containers

```html
<div style="color:green">
 <p> green text </p>
</div>
<p> not green text </p>
this is <span style="color:red"> red text </span>
```


## HTML Attributes and Ancor Tags
some HTML tage need to have an attribute to function
- `<img src="example.png" alt="some text">` the image tag
- `<a href="www.google.com"> text </a>` the anchor tag


## HTML Tables
```html
<table border=1>
	<thead>
		<th> colName 1</th>
		<th> colName 2</th>
	</thead>
	<tr>
		<td> entry 1 </td>
		<td> entry 2 </td>
	</tr>
	<tr>
		<td> entry 1 </td>
		<td> entry 2 </td>
	</tr>

</table>
```


## HTML Forms
#html/form 
HTTP (HyperText Transfer Protocol) methods:
- `GET` requests data from a source
- `POST` sends data to a server

e.g. a google search is a form with a single text field and a submit button

Inside an HTML Form are:
- **input** tags - dictates what the user can actually provide as information
- **label** tags - dictates what the user can see on the Form page

### example
```html
<form action="other_page.html">
  <lable for="fname">First Name:</label>
  <input type="text" id="fname" name="fname"> 
  <br>
  <lable for="email">First Name:</label>
  <input type="email" id="email" name="emailVar" > 
   <br>
  <lable for="pw">First Name:</label>
  <input type="password" id="pw" name="psdVar">
  
  <br>
  <input type="submit" value="text on the button">

</form>
```
`action` represents where the user goes after he submit the form
`<br>` new line
`id` idenify this tag
`name` a variable saving the value passed in this tag

### `input` types
- `type="radio"`  - give to input radio tags the same value of `name` (only one choose)
```html
<label for="out"> Outside: </label>
<input type="radio" id="out" name="loc" value="out"> <br>
<label for="in"> Outside: </label>
<input type="radio" id="in" name="loc" value="in"> <br>
```

- `<select>`
```html
<selct name="players" id="">
	<option value="player_1"> 1 </option>
	<option value="player_2"> 2 </option>
	<option value="player_3"> 3 </option>
</select>
```

- `<textarea>`
```html
<textarea name="" id="" cols="30" rows="10> </textarea>"
```


