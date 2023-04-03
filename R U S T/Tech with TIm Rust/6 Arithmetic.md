
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



