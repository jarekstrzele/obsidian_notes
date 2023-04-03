
```rust
fn main(){
    let x: u8 = 12 ; //0-255
    let y: i8 = 10; // -128-127
}

  = note: `#[deny(overflowing_literals)]` on by default
```
this code will generate an error


```rust
fn main(){
    let x: u8 = 12 ; //0-255
    let y: i8 = 10; // -128-127

	let z = x + y ;

	println!("{}", z) ;
}
let z = x + y ;
  |               ^ no implementation for `u8 + i8`
  
```
this code generates an error

`u8 + u8` -> `u8`
`f64 / f64` ->  `f64`
...

----
# Casting
```rust
let x = 255.0f32;
let y = 22i8 ;

///////////////////////
let x = 255.0_f32;
let y = 22_i8 ;

////////////////
let x = 255.0 as f32;
let y = 22 as i8 ;
//// explicite type conversion /////////
fn main(){
    let x = 127_000 as i64 ;
    let y = 10_i32 ;
    let z = x / (y as i64);
    println!("{}", z);
}

```

-----
# Input to int




