[[_ start Bootstrap]]


---

# Grids
Bootstrap's grid system is built with flexbox and allows yp to 12 columns across the page

`sm` small
`md` medium
`lg` large
`xl` xlarge
`xxl` xx large

Bootstrap will automatically handle the layout
`class="col"`

You will control the layout:
`class="col-*-*"`

1. create a row `<div class="row">`
2. add the desired number of columns: `col-*-*`
	- first star represents the responsiveness: sm, md, lg, xl, xxl
	- second star represents a nuber which should add up to 12 for each row

`col-sm-3`

```html
  <div class="row">
    <div class="col-sm-3 p-3 bg-primary text-white">.col</div>
    <div class="col-sm-3 p-3 bg-dark text-white">.col</div>
    <div class="col-sm-3 p-3 bg-primary text-white">.col</div>
    <div class="col-sm-3 p-3 bg-dark text-white">.col</div>
  </div>
```

```html
 <div class="row">
    <div class="col-sm-8 p-3 bg-primary text-white">.col</div>
    <div class="col-sm-2 p-3 bg-dark text-white">.col</div>
  </div>
```






	


