[[_HTML-W3school]]

---
# CSS Responsive
#w3school 
## What is Responsive Web Design?
- RWD makes your web page look good on all devices
- RWD uses only HTML and CSS
- RWD is not a program or JavaScript


## What is The Viewport?
It is user's visible area of a web page
The viewport varies with the device, and will be smaller on a mobile phone than on a computer scree

`<meta name="viewport" content="width=device-width, initial-scale=1.0">`

The `width=device-width` part sets the width of the page to follow the screen-width of the device
The `initial-scale=1.0` part sets the initial zoom level when the page is first loaded by the browser.

## What is a Grid-View?
A grid-view -> the page is divided into columns.
It often has 12 columns, and has a total width of 100%, and will shrink and expand as you resize the browser window.

### To buil a responsive grid-view
1. A HTML element has the `box-sizing: bordser-box` (This makes sure that the padding and border are included in the total width and height of the elements.)
```css
* {
	box-sizing: border-box;
}
```

2. Calculate the percentage for one column: 100%/12=8.33%
```css
.col-1 {width: 8.33%;}
.col-2 {width: 16.66%;}
.col-3 {width: 25%;}
.col-4 {width: 33.33%;}
.col-5 {width: 41.66%;}
.col-6 {width: 50%;}
.col-7 {width: 58.33%;}
.col-8 {width: 66.66%;}
.col-9 {width: 75%;}
.col-10 {width: 83.33%;}
.col-11 {width: 91.66%;}
.col-12 {width: 100%;}
```




