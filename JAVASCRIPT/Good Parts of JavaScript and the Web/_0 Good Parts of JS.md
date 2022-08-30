#javascript #network  #plurasight  #crockford_douglas

[[2 - And then there was JavaScript]]


---
# Start  Good Parts of JavaScript and the Web

## Programming Style & Your Brain

### Two System
[[Daniel Kahneman]] "Thinking Fast and Slow"
Metaphor of two System
###### gut
==one system== as the ==gut== (jelito, kiszka, wypatroszyć, instynktowny) it is intuitive, heuristic, associative VERY FAST
###### head
==two sytem== - as the ==head==, is the higher level one, analytic, algorithmic, reasoning an logic IS VERY SLOW

Kahneman discovered how these two system are connected:
- system two gets its assumptions, its working set from system one and is not aware of that connection system to, thinks it's getting this stuff from the cault of Deep Truth
- system on is an approximate system, sometimes gets things wrong, so from false input you get false output in logical system

### Visual Processing
#### an analogy
seeing reality - this problem is very hard
we and others living beings solved this problem but not in general way. We can see but some time we see wrong (illusions)
generally: to resist inconsistency (my state <-> word state) we misinterpret information from outside to stay consistence (it's not intentional)

> [!COMPUTER PROGRAMS]
> The most complicated things people make
> Programs should be perfect but they are not!!
> We have tests for imperfection but we have no tests for perfection


**Hunters and Gatherers**
Hunting and gathering was required a completely different set of skills  than makign things using computer programming

**Programming uses** HEAD [[#head]] but also GUT  [[#gut]] so we have to do tradeoff (kompromisy)


## JavaScript
JS has a lot of very good parts but also a lot of very bad parts
https://www.jslint.com/

in JS you have to write
```javascript
return {
	ok: true
};
//WOrks well in JavaScript
```
and not
```javascript
return
{
	ok: false
};
// SLIENT ERROR!!
```
because automatic semicolon insertion will put a semicolon after that return
`return; // semicolon insertion`
and
`{ ok: false; };`

> ALWAYS PUT YOUR CURLY BRACES ON THE RIGHT



## Programming Style
### switch  statement

we forgot how much time we spend chasing bufs

> A goof style can help produce better programs.
> Style should not be about personal preference and self-expression

> Medieval copyists introduced lowercase, word breaks, and punctuation -> these innovations helped reduce the error rate.

>Good use of style can help reduce the occurrence of errors.

**Programs must communicate clearly to people!!!!**


## Composition
Use elements of good composition where applicable.
For example, use a space after a comma, not before.

>
>Never rely on automatic semicolon insertion!!
>

Immediately Invocable Function Expressions:
```javascript
function (){
...
}(); // syntax error

(function (){
...
})(); //ok

(function (){
...
})()); //better

```

Always Use `===` not `==` -> you avoid transitivity problems (` 0 =='0' // true`)

Avoid forms that are difficult to distinguish from common errors.

Make your programs look like what they do.

## Scope
almost all modern languages have BLOCK scope but JavaScript has only FUNCTION scope
Some usefull roules:
1. declare all variables at the top of the function (JS reads in this way)
2. declare all functions before you call them

`for(var i ...){...}` Variable `i` is not scoped to the loop!!

LET THERE BE `let` because let will respect block scope 

### global variables
- are evile
- avoid them
- When using global variables, be explicit `UPPER_CASE`
- should be as rare as hens teeth and stick out like a sore thumb
- but in web app are necessary
- by default all variable are global, if you do not explicitly declare them in a function

### `new` prefix
forgetting `new` causes a constructor to clobber global variables without warning ; fixed in ES5/strict

Constructor functions should be named with InitialCaps and nothing else should be named with InitialCaps

> Write in a way that clearly communicates your intent!


# BAD STYLE

`++` operator is bad `x += 1` is good

> For no cost, by adopting a more rigorous style, many classes of errors can be automatically avoided.

## bad stylists
- under eductated
- old school
- thrill seeker
- exhibitionist


---
PERFORMANCE
- clean code is better than dirty code but optimized (Permature oprimization is the root of all evil)
- 






