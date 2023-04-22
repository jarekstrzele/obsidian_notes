#tuple #rust/tuple 
[[_ Rust Programming Tutorial]]
```rust
fn main() {
    
    let tupl1 = (1, "Test", true, 2.22, (20,30,"Tomorrow")) ;

    println!("tuple1.2 {}", tupl1.2) ;
    println!("tuple1.2 {}", (tupl1.4).2) ;
}
```


```rust

fn main() {
    
    let tupl1 = (1, "Test", true, 2.22, (20,30,"Tomorrow")) ;
    let (a,b,c, d, e) = tupl1 ;


    println!("tuple1.2 {}", tupl1.2) ;
    println!("tuple1.2 {}", (tupl1.4).2) ;
    println!("a {}", a) ;
    println!("b {}", b) ;
    println!("c {}", c) ;
    println!("d {}", d) ;
    
}

output:
tuple1.2 true
tuple1.2 Tomorrow
a 1
b Test
c true
d 2.22
```