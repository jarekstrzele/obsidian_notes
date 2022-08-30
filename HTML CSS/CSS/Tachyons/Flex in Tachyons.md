[[_ start Tachyons]]

---

# Flex in Tachyons

Jeżeli zadeklarujesz  `class=flex`  na pewnym elemencie HTML, to jego *children* będą ułożone w jednym wierszu:

Jeżeli dodasz do tego elementu `flex-wrap`, to jego *children*, o ile będą potrzebować więcej miejsca niż rodzić, zostają przeorganizowane do wielu wierszy.
(dodanie nie `class="flex flex-wrap"`, ale `class="flex flex-wrap-reverse"` odwróci kolejność)

Jeżeli użyjemy `class="flex flex-column"` to układ zmieni się  z wierszowego na kolumnowy (odpowiednio `class=flex flex-reverse` odwróci kolejność elementów)

```html
<!DOCTYPE html>
<html lang="en">
  <title> </title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://unpkg.com/tachyons/css/tachyons.min.css">
  <body>

  <div class="flex  flex-wrap">
    <div class="bg-black white outline w-25 pa3 mr2">
      <code>1</code>
    </div>
    <div class="bg-light-blue outline w-25 pa3 mr2">
      <code>2</code>
    </div>
    <div class="bg-yellow outline w-25 pa3 mr2">
      <code>3</code>
    </div>
    <div class="bg-pink outline w-25 pa3 mr2">
      <code>4</code>
    </div>
    <div class="bg-light-green outline w-25 pa3">
    <code>5</code>
    </div>
</div>
    
  </body>
</html>
```


`outline` linia poza granicą elementu
`w` = width
	- skala `w1   w2    ... w5` 
	- procentowo `w-10   w-20   w-25    w-100` (width:10%,  20%, 25%, 100%)
	- `ns` not-small (np. `w1-ns` = `width: 1rem`)(np. `w-30-ns)
	- `m` medium
	- `l` large
	- 
`pa1  pa2 p3 ... pa7` padding coraz większy
`ph1 ...` horyzontalny
`pv2 ....` wertykalny
`pl3` lewy
`pr4` prawy
`pt  pb` t górny, b dolny
to samo z `m` *margin*;  `ma` wszystkie marginesy













