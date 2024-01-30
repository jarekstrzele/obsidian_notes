

# variables
#rust/variable
```rust
let name: &str = "Alex";
let age: i32 = 32 ;
```

==Rust is a strongly typed language== - at compile time, Rust knows exactly the type of variable that you declare

Variable type is optional if it can be inferred.

Type can be specified explicity:
`let x: i64 = 45326445654 `

`#allow(unused_variable)` at the beginning of script so there will be no warrings.

###### follow SNAKE_CASE naming convention

```rust
//immutable
let length = 34 ;

//mutable
let mut length = 34 ;
length = 35 ;
```


##### shadowing is allowed
```rust
let color = "blue" ;
let color = "r"
```






