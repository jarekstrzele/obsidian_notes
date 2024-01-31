

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

###### shadowing is allowed
```rust
let color = "blue" ;
let color = "red" ;
println!("Color is {}", color) ; // --> red

// event that:
let color: !32 = 86 ;
let color: $str = "blue"
```

##### declaring multiple variables simultaneously
```rust
let (a,b,c) = (2,3,4) ;
```

---
# scalar data types

## integer
`i` signed - `8 16 32 64 128`
`u` unsiged = `8 16 32 64 128`
`isize` and `usize` size of integer depending on the size that the machine has

## float
`f32`, `f64`

type casting:
- `let pi: f32 = 4  ; // mismatched types error `
- `let pi: f32 = 4.0  ; // ok `

`let million: i32 = 1_000_000 ; // ok`

## Boolean
`true`, `false`


## character
`let char: char = 'A' ;`

-------
# Strings




































