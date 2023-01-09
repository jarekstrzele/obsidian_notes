[[Container]]
[[Grids]]

---


# Start Bootstrap 5
- bootstrap is a free font-end framework  for faster and easier web developlment
- it includes HTML, CSS based templates
- you can create responsive designs

>**responsive web design** is about creating web sites which  automatically adjust themselves to look good on all devices , from small phones to large desktops
>

> **CDN** CDN stands for content delivery network
Most often, it is a set of linked servers which accelerate giving the data (photo, video, scripts) back to the user. CDN servers are placed as close as possible to the end audience.
> **CDN** takes popular content to cache servers where it is accumulated, temporarily stored (cached) and given at future requests.

## CDN Bootstrap
```html
<!-- Latest compiled and minified CSS -->
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet">

<!-- Latest compiled JavaScript -->
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js"></script>
```


## The first web

1. add the html5 doctype (`<!DOCTYPE>`)
2. Add `<meta name="viewport" content="width=device-width, initial-scale=1">` for mobile. Mobile-first styles are parto of the core framework.
The `width=device-width` part sets the width of the page to follow the screen-width of the device (which will vary depending on the device).

The `initial-scale=1` part sets the initial zoom level when the page is first loaded by the browser.

3. Bootstrap 5 requires a containing element to wrap site contents
`.container` a responsive fixed width container
`.container-fluid` a full width container


----
# Styling tags
`<abbr>`
`<blockquote>`
`<dl>`
`<mark>`
`<code>`
`<kdb>`
`<pre>`

---
# Spacing
The classes are named using the format:
`{property}{sides}-{size}` for xs and
`{property}{sides}-{breakpoint}-{size}` for sm, md, lg, xl, and xxl.

Where **property** is one of:
`m` - for classes that set margin
`p` - for classes that set padding

Where **sides** is one of:
`t` - for classes that set margin-top or padding-top
`b` - for classes that set margin-bottom or padding-bottom
`s` - (start) for classes that set margin-left or padding-left in LTR, margin-right or padding-right in RTL
`e` - (end) for classes that set margin-right or padding-right in LTR, margin-left or padding-left in RTL
`x` - for classes that set both *-left and *-right
`y` - for classes that set both *-top and *-bottom
`blank` - for classes that set a margin or padding on all 4 sides of the element

Where **size** is one of:
`0` - for classes that eliminate the margin or padding by setting it to 0
`1` - (by default) for classes that set the margin or padding to $spacer * .25
`2` - (by default) for classes that set the margin or padding to $spacer * .5
`3` - (by default) for classes that set the margin or padding to $spacer
`4` - (by default) for classes that set the margin or padding to $spacer * 1.5
`5` - (by default) for classes that set the margin or padding to $spacer * 3
`auto` - for classes that set the margin to auto










