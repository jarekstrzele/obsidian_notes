[[Bootstrap]]


----

## NAVBARS
are navigational bars that you will often see on the top of a website

-> components -> navbars
https://getbootstrap.com/docs/3.4/components/#navbar

```html
 <nav class="navbar navbar-default navbar-fixed-top">
  <div class="container">
    <div class="navbar-header">
      <a href="#" class="navbar-brand">Company</a>
     </div>

     <ul class="nav navbar-nav">
       <li><a href="#">Item One</a>
       <li><a href="#">Item Two</a>
      </ul>

      <ul class="nav navbar-nav navbar-right">
        <li> <a href="#"> On the right </a> </li>
        </ul>
    </div>    
</nav>
```

## Fixing on top

If you want the actual navbar to be scroll along with you as u=you go through the page:
` <nav class="navbar navbar-default navbar-fixed-top">`
`navbar-fixed-top`

## Inverting color
if you wan to invert colors:
` <nav class="navbar navbar-default navbar-inverse navbar-fixed-top">`

## Collapsing navbar
```html
   <div class="navbar-header">
      <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1" aria-expanded="false">
        <span class="sr-only">Toggle navigation</span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
      </button>
   
```

Anything inside of `collapse navbar-collapse`  *class* goes into the "humburger"
i.e.
```html
<div class="container collapse navbar-collapse">
    <div class="navbar-header">
      <a href="#" class="navbar-brand">Company</a>
     </div>

     <ul class="nav navbar-nav">
       <li><a href="#">Item One</a>
       <li><a href="#">Item Two</a>
      </ul>

      <ul class="nav navbar-nav navbar-right">
        <li> <a href="#"> On the right </a> </li>
         <li> <a href="#"> two the right </a> </li>
        </ul>
    </div>    
```
You have to you JS script to make "humburger" working


