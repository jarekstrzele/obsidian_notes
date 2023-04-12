[[_ Rust Programming Tutorial]]
```rust
fn main() {
    let x = 45 ;

    println!("The value of x: {}", x) ;

}

output: The value of x: 45
```



> 
> in Rust all variables by default you define are immutable
> 
```rust
fn main() {
    let x = 45 ;
    println!("The value of x: {}", x) ;

    x = 60 ;
    println!("The value of x: {}", x) ;
}

output:  x = 60 ;
  |     ^^^^^^ cannot assign twice to immutable variable
```

to make `x` mutable:
```rust
fn main() {
    let mut x = 45 ;
    println!("The value of x: {}", x) ;

    x = 60 ;
    println!("The value of x: {}", x) ;

}

output:
The value of x: 45
The value of x: 60
```


---
# Variable Data Types
```rust
fn main() {
    let x:i32 = 15 ;
    let y: i64 = 11222 ;
    let z: f64 = 987654.4321 ;
    let yes: bool = true;

   
    println!("The value of x, y, z, yes: {}, {}, {}, {}", x, y, z, yes) ;

}

output: The value of x, y, z, yes: 15, 11222, 987654.4321, true
```









