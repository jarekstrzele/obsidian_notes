
[[_ Introduction to CSS layout]]


---
## nowa właściwość `flex-direction`
 `flex-direction` okreśła kierunek osi głównej `main axis` (domyślna wartość to `row`)
CSS: `flex-direction: value;`
`value`:
- `row` wierszowy układ
- `row-reverse` układ wierszowy odwrócony
- `column` układ kolumnowy
- `column-reverse` układ kolumnowy odwrócony

przykład:
```css
.content {
  width: 200px;
  height: 200px;
  border: 1px solid #c3c3c3;
  display: flex;
}

.box {
  width: 50px;
  height: 50px;
}

#col-rev {
  flex-direction: column-reverse;
}

#row-rev {
  flex-direction: row-reverse;
}

.red {
  background-color: red;
}

.lightblue {
  background-color: lightblue;
}

.yellow {
  background-color: yellow;
}
```


```html
<h4>This is a Column-Reverse</h4>
<div id="col-rev" class="content">
  <div class="box red">A</div>
  <div class="box lightblue">B</div>
  <div class="box yellow">C</div>
</div>
<h4>This is a Row-Reverse</h4>
<div id="row-rev" class="content">
  <div class="box red">A</div>
  <div class="box lightblue">B</div>
  <div class="box yellow">C</div>
</div>
```
