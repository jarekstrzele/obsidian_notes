#rust/memory #rust/heap #rust/stack

https://www.youtube.com/watch?v=-6cnnNlAvNk&list=PLzMcBGfZo4-nyLTlSRBvo0zjSnCnqjHYQ&index=9


In Rust we have two different sections of RAM:
- ==stack== - LIFO (it is a traditional stack, like plates in stack ), it is the fastest, only fixed-size elements
- ==heap== - it is not traditional heap


--------------
# Stack is faster

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
# Heap is slower
allocate the memory -> search a space to memory the data
```rust
fn main(){
	let x = 2 ;
	let string = String::form("hello") ;
}
```
- `x` will be written on the top of the stack,
- the value of `string` will be written in the heap because you could change the length of this string and 
- the `string` will be written on the stack and its value will be the memory address of the heap where `"hello"` is written






