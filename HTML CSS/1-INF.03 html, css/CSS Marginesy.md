[[_ CSS]]

[[Model Blokowy CSS]]

---
# Marginesy

## zewnętrzne `margin`
oddziela element od innych elementów

`selector {margin-pozycja: values;}`

`pozycja`:
- `top`
- `bottom`
- `left`
- `right`

`value`: liczba z jednostką (np. 10px, 12pt) lub `auto`

samo `margin`:
`selector{margin: wszytkie_jednakowe;}`
`selector{margin: góra_i_dół Lewo_i_prawo;}`
`selector{margin: góra lewo_i_prawy dół;}`
`selector{margin: góra prawy dół lewy;}`


## wewnętrzne `padding`
przestrzeń między zawartością o granicą/obramowaniem
syntaktyka podobna jak przy `margin` tylko zamiat `margin` występuje `padding`

```html
<!DOCTYPE html>
<html>
<head>
</head>
<body>
  To jest zwykły tekst przed divem
  <div  style="border: 5px solid  blue; border-size: 1px; margin: 10pt 20pt" >
    <p style="border: dotted 2px red; padding: 10pt"> Paragraf 1 Co tam lorem ipsum <p>
    <p style="border:  7px groove orange; padding-left:5cm; padding-top:1cm; padding-bottom:10mm; margin: 20px;"> Paragraf 2 </p>
    
    
  </div>
</body>
</html>
```




