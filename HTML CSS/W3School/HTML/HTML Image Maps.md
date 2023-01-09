[[_HTML-W3school]]
[[Images]]
#html/image 

---
# HTML IMAGE MAPS
WIth HTML image maps, you can create clikable areas on an image.

`<map>`:
- defines an image map
	- an image map is an image with clockable areas
		- the areas are defined with ione or more `<area>` tags


```html
<img src="workplace.jpg" alt="Workplace" usemapd="#workmap">

<map name="workmap">
	<area shape="rect" coords="34,44,270,350" alt="Computer" href="computer.htm">
	<area shape="rect" coords="290,172,333,250" alt="Phone" href="phone.htm">
	<area shape="circle" coords="337, 300,44" alt="Coffee" href="coffee.htm">
	</map>
```

The idea behid an image map:
>you should be able to perform different actions depending on where in the image you click

To create an image map you need an image, and some HTML code that describe the clickable areas.

1. image is inseted using `<img ... usemap="#name_of_the_image_map"`
2. creae image map `<map name="name_of_the_image_map">`
3. add the clickable areas `<area>`
	1. shape of clickable areas:
		1. `rect`
			1. the coordinates come in pairs, one for x-axis and one for the y-axis
			2. `34,44` 34 pixels from the left margin and 44 picels from the top
			3. `270, 350` 270 pixels from the left margin and 250 pixels from the top
		2. `circle`
			1. center of the circle `337,300`
			2. then specify the radius of the circle `44`
			3. `coords="337, 300, 44"`
		3. `poly`
		4. `default`