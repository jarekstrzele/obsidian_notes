[[_ Ultimate Rust Crash Course]]


# Closure
#rust/closure 
>[!info] Closure
>it is an anonumous function that can borrow or capture somedata from the scope it is nested
>**a closure will borrow a reference to values in the enclosing scope**


#### `|x, y| {x + y}` - two params
#### `|| {x + y}` - no params

```rust
let add = |x,y| {x+y} ;
add(1,2) ; //return 3
```

**borrowing**
```rust
let s = "sometext".to_string();
let f = || {
	println!("{}", s) ;
}
f();
```
- that closure borrows a reference to `s`
- we assign the closure to the variable `f` and whenever  we call `f()` it prints that text
- you can't send this over to another thread because another thread might live longer than this thread

**move semantics**
```rust
let s = "sometext".to_string();
let f = move || {
	println!("{}", s) ;
}
f();
```
- that closure takes ownership of  `s`, so `s` will live untile the closure itself





# Threads
#rust/thread



