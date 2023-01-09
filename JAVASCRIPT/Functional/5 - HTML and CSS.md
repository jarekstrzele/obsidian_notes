[[0- Intro functional programming (beginner udemy)]]i


[[5 Generating HTML and CSS]]
[[5 Transforming Data to HTML]]


---
# Tachyons CSS Library
#css/tachyons

`css files` are goint to be longer and longer (nobody delete css rules)

In Tachyons  you combine or compose a bunch of simple, very generic classes to get the exact button you are looking for.

https://tachyons.io/

```html
<head> 
	
<link rel="stylesheet" href="https://unpkg.com/tachyons@4.12.0/css/tachyons.min.css"/>
```

```html
...
<button class="pa3 bg-blue white"> Save</button>
<button class="ph3 pv2"> Save</button>

```
`p` - Padding
`a` - all sides
`3` - third scale
`h` - horizontally
`v` - veritcally
`bg` background color
`white` color

```html
<button classs="ph2 pv2 bg-blue white bn br4"> Save </button>
```
`b` border
`n` none
`br4` border radius 4

to interact with button add new class `pointer` or `dim`

