[[jQuery]]

[[jQuery Project]]

---
# jQuery Events
https://api.jquery.com/category/events/

## click
in js file:
```javascript
$('h1').click(function(){
  console.log('There was a click!')
})


$('li').click(function(){
  console.log('any li was clicked')
})
```

a click changing `h1`:
```js
$('h1').click(function(){
  $(this).text("I was changed")
})
```




## key press
`input 0`  is a `<input type="text" ...`
```js
$('input').eq(0).keypress(function(){
  $('h3').toggleClass("turnBlue")
})

```

```js
$('input').eq(0).keypress(function(){
  console.log(event)
})

```
The object event has a property `which` with a number of the written letter. e.i. 'enter' === 12

```js
$('input').eq(0).keypress(function(event){
  if (event.which === 13) {
    $('h3').toggleClass('turnBlue');
  }
})


```

## on(event, function)
```js
$('h1').on('dblclick', function(){
  $(this).toggleClass('turnBlue');
})

```

```js
$('h1').on('mouseenter', function(){
  $(this).toggleClass('turnBlue');
})
```



https://api.jquery.com/category/effects/

```js
$('input').eq(1).on('click', function(){
  $('.container').fadeOut(3000)
})

```