[[język HTML 5]]
# Elementy składowe strony WWW

## Elementy blokowe dokumentu HTML

==pragraf==   `<p> ...   </p>`
==nagłówki== `<h1> ... </h1` - `<h6> ... </h6>`
==pogrubienie==   `<b> ... </b>` (np. słowa kluczowe) 
				`<strong> ... </strong>`
==kursywa==  `<i> .. </i>` (np. termin techniczny)
		   `<em> ... </em>>`

==podkreślenie== `<u> ... </u>`

==pozioma linia== `<hr>`
==nowa linia== `<br>`

==komentarz== `<!-- ... -->`


```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Elementy blokowe</title>
</head>
<body>
  
  <p> jestem paragrafem </p>
  <p> jestem paragrafem </p>
  
  <br>
  <hr>
  
  <h1> H1 </h1>
  <h6> h6 </h6>
  zwykły tekst
  <b> pogrubiony </b> tekst <br>
  <u> podkreślony </u> tekst <br>
  <i> pochylony </i> tekst
  <p></p>
  
  
</body>
</html>
```


---

## Znacznik `<div>`
`<div> ... </div>` od _divide_ - (po)dzielić, rozbić, pokrajać, porozdzielać

- grupuje wiele różnych elementów na stronie
- pozwala zdefiniować dowolny układ strony
- tworzy oddzielny blok
- pozwala dzielić stronę na bloki takie jak: magłówek, panele, paski nawigacji, ...
- jest formatowany i pozycjonowany za pomocą arkuszy stylów CSS

jego odpowiednik liniowy to `<span> ... </span>`

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Znacznik DIV</title>
</head>
<body>
  <div style='background: orange'> Jestem div 1
    <p> A to jest jakiś tam tekst </p>
  </div>
  <br>
  <hr>
  <div style='background: red'> Jestem divem 2 <br> <br>
    <div style='background: blue; color: white'> 
      <p> jakiś nam paragraf </p>
      Jestem pierwszym divem w div 2
      <br>
      <br>
    </div>
    
    <div style='background: green'>
      <p> to jest paragraf w <p>
      jestem drugim divem w div 2 <br>
      <span style="color: orange" > a ten tekst jest w </span> znaczniku span
    </div>
    
  <div>
   
  
</body>
</html>
```


---

## Znaczniki semantyczne podziału strony
czyli `<div>` z nazwą zrozumiałą dla człowieka i z predefiniowanymi funkcjonalnościami

`<header> ... </header>` 
- powinien zawierac  część nagłówkową strony lub sekcji
- może być umieszczany w innych elementach
- może zawierać inne elementy
- `id` ten atrybut pozwoli łatwo zidentyfikować dany nagłówek na stronie

`<nav> ... </nav>`
- blok nawigacyjny
- powinien zawierać zbiór odnośników
- w jednym dokumencie może być wiele bloków nawigacyjnych
- widoczny w sekcji nagłówka i w stopcie
- może być umieszczany w innych elementach
- może zawierać inne elementy

`<section> ... </section>`
- logiczne części strony
- zawierają treść o określonej tematyce
- może być umieszczany w innych elementach
- może zawierać inne elementy
- powinien zawierać tytuł

`<article> ... </aricle>`
- treść stanowi spójną całość
- treść jest niezależna od innych treści w dokumencie (mogłaby być samodzielną stroną)
- powinien posiadać nagłówek, treść, stopka
- może być umieszczany w innych elementach
- może zawierać inne elementy
 
`<aside> ... </aside>`
- zamknięty fragment 
- zawiera różne treści (np. cytaty, przypisy, dygresje, ....)
- swoisty panel boczny

`<footer> ... </footer>`
- stopka dokumentu lub sekcji
- zawiera informacje o prawach autorskich, danych do kontaktu, ....											 
![[semantyczne_znaczniki.excalidraw|700]]

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Elementy blokowe</title>
  
  <style>
    aside {
  width: 20%;
  padding-left: 115px;
  margin-left: 5px;
  float: right;
  font-style: italic;
  background-color: orange;
}
    
  </style>
</head>
<body>
  <div>
    <header id="zoo_w_olsztynnie">
      <h1>Zoo  <h1>
      <h2>w Olsztynie</h2>
        <p> Najlepsze zoo w Polsce </p>
    </header>
        
   <nav>
    To jest nawigacja
    <ul>
      <li> droga do zoo </li>
      <li> historia zoo </li>
      <li> bilety do zoo </li>
      <li> imprezy integracyjne </li>
    </ul>
     
   </nav>
        
  </div>
      
  <div>
    <section>
      <h3> Czy warto przyjechać do nas? </h3>
        <article>
          <h3> Co o nas pisze konkurencja </h3>
          <p>Integer porta dui a velit fringilla, ac laoreet lacus sagittis.  Aenean lobortis, dolor eget molestie tristique,   quam orci congue magna, quis rutrum lorem mi sit amet velit.  Curabitur quis tortor erat. Sed semper posuere metus,             a finibus justo ultricies at. Nunc sed ipsum vitae nisi consequat      sollicitudin. Curabitur et ipsum sed enim efficitur hendrerit vel at dui.   Suspendisse potenti. Vivamus pretium sodales justo, sed cursus nibh tristique     eget. Nam dapibus mattis nulla, eget tempor massa consequat et.       Donec vel magna magna. Nullam sodales risus id velit hendrerit, 
            nec convallis quam eleifend. Duis ullamcorper eu nunc nec sodales.      Sed ac accumsan risus. Cras maximus libero vel felis rutrum, ac auctor sem mattis.
          Aliquam condimentum vulputate feugiat.
         </p>
          
         
      </article>
      
      <article>
          <h3> Co o nas myślą nasi klienci </h3>
            <p> Duis molestie dui at facilisis iaculis. Donec pulvinar, nibh a vehicula 
              blandit, magna purus efficitur nibh, et laoreet arcu arcu vel libero.
              Maecenas fermentum vitae nunc id semper. Sed tempor aliquet sagittis. 
              Cras consequat ultricies ligula. Phasellus ullamcorper libero non posuere feugiat. Ut eget diam condimentum, fermentum sapien et, tempor nisl. Donec lacus felis, hendrerit eu tellus ac, volutpat rhoncus massa.
            </p>
                       
       </article>
          <footer> A to jest footer do sekcji 1</footer>
    
    </section>
    
    <aside>
      <h5> Taki mały dodatek <h5>
        <p> To jest taki mały dodatek informacyjny o zoo </p>
      
    </aside>
    
  </div>
  
  
  
  
</body>
</html>
```








