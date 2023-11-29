[[_ 0 Django 4]]


# CSS
#css 
Cascading Style Sheets - designed to separate out the styling of the HTML elements into a separate document

## HTML Attribute
`<p style="color:red"> mmm </p>`

## CSS files
in .html
```html
<link rel="stylesheet" href="styles.css">

</head>
```
in css file
```css
h1{
  color:goldenrod;
}
```

```csss
.myclass{

}

#my_id{

}
```

```css
  

span{

background-color: red;

}

  

div{

background-color: greenyellow;

border-color: orange;

border-width: 10px;

border-style: dashed;

}
```


## FONTs
```css
h1{
 font-family: Tahoma;
 text-align: center;
 
}
```

https://developer.mozilla.org/en-US/docs/Web/CSS/font-size

`em` depends on the default size of font on the webpage

Google Fonts

zadanie
```css
h1 {
    font-family: Arial;
}

p{
    font-size: 1em;
}

#small{
    font-size: 0.5em;
}
```

```html
<!-- TASK: Fill the html and css files.
# MAKE SURE TO READ THE FULL INSTRUCTIONS ABOVE CAREFULLY, AS THE EVALUATION SCRIPT IS VERY STRICT.
# Link to Solution: Solution: https://gist.github.com/Pierian-Data/114b027131f6ec58392657ca14191b81
 -->
 
 <h1>To jest h1</h1>
 
 <p>to jest 
 <div id="small">paragraf
 </div
 </p>
 
 
 
 
 
 
```

## CSS Model Box
![[css_box_model.excalidraw | 700]]

```css
#down{
	text-align: center;
	border: 10px solid red;
	margin-left: 100px;
	padding-top: 50px;
	
}
```






