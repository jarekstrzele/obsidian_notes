[[JavaScript]]

---
# D O M
[[#Grabbing HTML elements]]
[[#To interact with object - intro]]
[[#EVENTS]]



Browsers will construct the Document Object Model, which basically means storing all the HTML tags as JavaScript objects

`console.log(document)`  or `document` -> we can see HTML code
`console.dir(document)` -> to see the actual objects; we can see the DOM

The DOM allw us to use JS to interact with the web page.
The DOM is enormous.

---

## Grabbing HTML elements
__Some important document attributes:__
- document.URL
- document.body
- document.head
- document.links

__Some methods for grabbing elements from the DOM__:
- document.getElementByID()
- document.getElementByClassName()
- document.getElementsByTagName()
- document.querySelector() -> the first object matchin the key style selector  (CSS)
	- document.querySelector("#pickme") # -> the first elem with `id="pickme"` 
- document.querySelectorAll() -> all objects matching the style selector (CSS)
	- document.querySelectorAll(".myul") # -> list of all elem which belong to `class="myul"`

---


### To interact with object - intro
```js
var myheader = document.querySelector("h1")
myheader.style.color = 'red';

```


We can change the text, html content or attribute
- `myvar.textContent` returns just the text
- `myvar.innerHTML` returns the actual html
- `myvar.getAttribute()` returns the original attribute
- `myvar.setAttribute` allows to set an attribute

```js
var p = document.querySelector('p');

// change the text of the paragraph
p.textContent = "SOmthing new";
p.innerHTML = "<strong> I'm bold </strong>"

var my_h2 = document.querySelector("#overview")
var my_h2_a = my_h2.querySelector("a")
my_h2_a.getAttribute("href"); # -> address url
my_h2_a.setAttribute("href", "http://google.pl")



```


---

## EVENTS
Many times we only want the interaction to occur on a particular event, such as a click or a hover.

We achieve this by adding an Event Listener.
The JS will be "listening" for an event to occur and then execute a function when it happens.

generally
```js
myVar.AddEventListener(event, func);
```

example
```js
var head = document.querySelector('h1');
head.addEventListener("click", changeColor);
```

events - examples:
- clicks,
- hovers,
- double clicks,
- drags,
- ...



---

```js
var headOne = document.querySelector("#one");

var headTwo = document.querySelector("#two");

var headThree = document.querySelector("#three");

  

headOne.addEventListener('mouseover', function(){

headOne.textContent = "Mouse Currently Over";

headOne.style.color = 'red';

})

  

headOne.addEventListener('mouseout', () => {

headOne.textContent = "Hover Over me!";

headOne.style.color = "black";

})

  

headTwo.addEventListener('click', function(){

headTwo.textContent = "Clicked on";

headTwo.style.color = 'blue';

})

  

headThree.addEventListener('dblclick', function(){

headThree.textContent = "I was double clicked";

headThree.style.color = 'green';

})
```









