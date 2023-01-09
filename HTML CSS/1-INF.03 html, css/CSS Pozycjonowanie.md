[[_ CSS]]


----
# Pozycjonowanie
czyli określanie położenie elementu na stronie


## `position`
`selector{position: rodzaj; parametry;}`

**rodzaj** (określa sposób pozycjonowanie):
- `static` przywraca normalne pozycjonowanie (użycie w atrybucie `style` znacznika)
- `relative` pozwala przesunąć wybrany element w inne miejsce w stosunku do położenia pierwotnego (parametry określają sposób przesunięcia; np. `left:30px;` doda 30px w lewo do pierotnego położenia
- `absolute` przesuwanie elementu określane względem brzegu strony lub bloku (o ile element jest w bloku); parametry określą "sztywne" połóżenie tego elementu
- `fixed` ustala położenie ZAWSZE względem krawędzi przeglądarki (element będzie zawsze widziany w tym miejscu)

**parametry**
`kierunek: o ile przesunąć`
- `left: value` przesunąć o określoną wartość w stosunku do lewej krawędzi położenia pierwotnego
- `right: value` przesunąć o określoną wartość w stosunku do prawej krawędzi położenia pierwotnego
- `top: value` przesunąć o określoną wartość w stosunku do górnej krawędzi położenia pierwotnego
- `bottom: value` przesunąć o określoną wartość w stosunku do dolnej krawędzi położenia pierwotnego
`auto` wartość będzie domyślna
wartość ujemy to przeciwny kierunek

można parametry łączyć (`left ` ma pierszeństwo przed `right`, a `top` przed `bottom`)

`{ position: absolute;  left: 150px; bottom:100px;}`


```css
.pudelko{
  border: 2px solid red;
  width: 100pt;
  height: 90px;
  background-color:blue;
  padding: 25px; color:white
}

.blok{
  background-color:green;
}

.blok1{
  position: relative; left:150px;
}

.blok2{
  position: absolute; left:100px;
}
.blok3{
  position: fixed; left:100px;
}

```


```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
</head>
<body>
  
   <div class="pudelko blok1" >
     1111
  </div>

   
   <div class="pudelko blok1" >
     22222
  </div>
  
  <div class="pudelko blok2" >
     <div> 333333 <div>
  </div>
       
       
  <div class="pudelko blok" >
     44444
  </div>
  
  <div class="pudelko blok1" >
     55555
  </div>
  <div class="pudelko blok" >
     66666
  </div>
  <div class="pudelko blok" >
     777777
  </div>
  
  
  
  <div class="pudelko blok" >
     8888
  </div>
</body>
</html>
```