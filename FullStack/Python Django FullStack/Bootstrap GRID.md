[[Bootstrap]]



# Bootstrap GRID
- the grid system for Bootstrap is one of its most fundamental features
- so far we've mostly seen  convienient tools that bootstrap provides through classes
- the grid system goes much further than that (websites will look good across mutliple devices of mutliple screen sizes)

**GRID**
- We split the entire screen into 12 available columns
- you can combine: 6x2=12, 4x4, 3x4, 2x6, ....
- the grid system call will make use of the `class="row"`
- inside of a row class, we then have the following format `col-ScreenSize-NumberOfColumns`
	- `ScreenSize`: extra large, large, medium, small, extra small
	- `col-md-6` screensize is medium and  six columns (6x2)
	- 

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <!-- Latest compiled and minified CSS -->
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">

  <!-- Optional theme -->
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap-theme.min.css" integrity="sha384-rHyoN1iRsVXV4nD0JutlnGaslCJuC7uwjduW9SVrLvRYooPp2bWYgmgJQIXwl/Sp" crossorigin="anonymous">

  <!-- Latest compiled and minified JavaScript -->
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/js/bootstrap.min.js" integrity="sha384-Tc5IQib027qvyjSMfHjOMaLkfuWVxZxUPnCJA7l2mCWNIpG9mGCD8wGNIcPD7Txa" crossorigin="anonymous"></script>
  
  
  <style>
    .boxy{
      background: #b3ddff;
      border: 2px solid black;
    }
  </style>
    <title>JS Bin</title>
  </head>

  <body>
    <div class="container">
      <div class="row">
        <div class="col-lg-6 boxy"> COL lg 6 </div>
        <div class="col-lg-6 boxy"> COL lg 6 </div>
        
      </div>
  
        <div class="row">
        <div class="col-md-4 boxy"> COL m 4 </div>
        <div class="col-md-4 boxy"> COL m 4 </div>
        <div class="col-md-4 boxy"> COL m 4 </div>
      </div>
      
        <div class="row">
        <div class="col-xs-4 boxy"> COL xs 4 </div>
        <div class="col-xs-4 boxy"> COL xs 4 </div>
        <div class="col-xs-4 boxy"> COL xs 4 </div>
      </div>
    
    </div>
   
  </body>
</html>
```


You can write "if":
```html
<div class="row">
	<div class="col-lg-3 col-sm-6"> One </div>
	<div class="col-lg-3 col-sm-6"> One </div>
	...
</div>
```
If a screen is large divide it into tree, but if it is small, divide it into six













