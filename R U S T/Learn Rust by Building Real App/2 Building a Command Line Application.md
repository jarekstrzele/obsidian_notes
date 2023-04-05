#rust 
read the input from console and ouput some answers

CONCEPT:
- functions
- basic data types
- standard library
- memory ownership

----
# Basic data types
- booleans
- characters
- integers
- floats
- 

## integers
`u` unsigned integer POSITIVE only
`i` signed integer
`u8, i8` $0$ (one bite)
`u16, i16` $00$
`u32, i32` $0000$
`u64, i64` $00000000$
`u128, i128` $0000000000000000$


`usize` or `isize`  architecture dependent types 


## float
`f32`
`f64`

## boolean
`bool` $0$

# char
`char` $0000$

----------
# Function
`cargo new mars_calc`
`cd mars_calc`
`cargo run`

#### `fn main`
it is always the first code that runs - the entry point

==use snack_case_convention== to name functions

>[!important] `return`
>The last expression in every function that doesn't have a semicolon at the end  is AUTOMATICALLY returned


```rust
fn main() {
    println!("Hello, world!");
    calculagte_weight_on_mars(100.0) ;
}

fn calculagte_weight_on_mars(weight: f32) -> f32{
    50.0
}
```



