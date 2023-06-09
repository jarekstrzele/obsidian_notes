[[_ Ultimate Rust Crash Course]]


# Closure
#rust/closure 
>[!info] Closure
>it is an anonumous function that can borrow or capture somedata from the scope it is nested
#### `|x, y| {x + y}` - two params
#### `|| {x + y}` - no params


```rust
let add = |x,y| {x+y} ;
add(1,2) ; //return 3
```

# Threads
#rust/thread



