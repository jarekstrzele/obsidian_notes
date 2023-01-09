[[FullStack/Python Django FullStack/CSS]]

---
[[Bootstrap Button]]
[[Bootstrap Form]]
[[Booststrap NavBar]]
[[Bootstrap GRID]]

https://getbootstrap.com/docs/3.4/getting-started/
---

#bootstrap

==Framework==
- inversion of control (you're giving up control to the framework),
- default behavior (framework is going to have some sort of default behaviour
- it's a non modifiable framework code - Non-modifiable Framework Code

---
# BOOTSTRAP
==class="container" is very often used.!!!!!!!!!!!!!!!==
https://getbootstrap.com/

To __use bootstrap__ you can:
- download it or
- Booststrap CDN (links like google fonts)

https://getbootstrap.com/docs/5.1/getting-started/introduction/

---
> A key feature of bootstrap are its default classes.

```html
 <link rel="stylesheet"  href="https://cdn.jsdelivr.net/npm/bootstrap@3.4.1/dist/css/bootstrap.min.css"  integrity="sha384-HSMxcRTRxnN+Bdg0JdbxYKrThecOKuH5zCYotlSAcp1+c8xmyTe9GYg1l9a69psu" crossorigin="anonymous"> 

<h1> Bootstrap!!! </h1>


        <div class="container">
            <h1> Hello WOlrd</h1>

        </div>
```

## Grids
>The grid system provides the core mechanism by which using Bootstrap alllows websites to look good across multiple devices of multiple screen sizes

- we split the entire screen into 12 available columns
- W can use any combination of numbers that will eventually add up to 12 columns
- 6x2(po dwie dolumny)
- 4x3(jedno pole trzy kolumny)
- ...
- 2x6(jedno pole 6 kolumn)

The grid system call will make use of the `class='row'`.
Inside of a row class, we then have the following format:
	- col-ScreenSIze-NumberOfColumns
	- `col-md-6` when the screen size is of a mediem screen size -> six cols

```html
  <body>
    <style>
     .boxy{
        background: #b3ddff;
        border: 2px solid black;
}
    </style>
      <div class="container">
        <div class="row">
           <div class="col-lg-4 boxy"> COL Large 4 </div>
        <div class="col-lg-4 boxy"> COL Large 4 </div>
        <div class="col-lg-4 boxy"> COL Large 4 </div>
                
       </div>
     </div>


    </body>

```













