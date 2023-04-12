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










