#rust/memory #rust/heap #rust/stack

https://www.youtube.com/watch?v=-6cnnNlAvNk&list=PLzMcBGfZo4-nyLTlSRBvo0zjSnCnqjHYQ&index=9


In Rust we have two different sections of RAM:
- ==stack== - LIFO (it is a traditional stack, like plates in stack ), it is the fastest, only fixed-size elements
- ==heap== - it is not traditional heap


--------------
# Stack

```rust
fn main(){
	let x = 2 ;
	let y = x ;
}
```
first:
	address: 0, name: x, value: 2
second:
	address: 1, name: y, value 2 (this is a copy of the x value)

The main function ended -> second pop(), first pop()

----------------
```rust
fn main(){
	let x = 2 ;
	let y = x ;
	example() ;
}

fn example(){
	let a = "true" ;
	let b = false ;
}
```

first:
	address: 0, name: x, value: 2
second:
	address: 1, name: y, value 2 (this is a copy of the x value)
third:
	address: 2, name: a, value: "true"
fourth:
	address: 3, name: b, value: false

first the example function finished: b pop(), a pop()
second the main function finished: y pop(), x pop()


-------
# Heap







