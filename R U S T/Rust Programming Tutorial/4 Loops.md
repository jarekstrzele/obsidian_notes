https://www.youtube.com/watch?v=dUW7FB_ajMs&list=PLVvjrrRCBy2JSHf9tGxGKJ-bYAN_uDCUL&index=7

[[_ Rust Programming Tutorial]]

# Infinite loop
```rust
fn main() {
    let mut n =0 ;
    
    loop {
        n += 1;
        println!("n={:?}", n );
    }
}
```

```rust
fn main() {
    let mut n =0 ;
    
    loop {
        n += 1;
        
        if n == 7 {
            continue ;
        }

        if n > 10 {
            break ;
        }
        println!("n={:?}", n );
    }

}

```


-------
# While
```rust
fn main() {
    let mut n =0 ;
    
    while n <= 50 {
        if n % 5 == 0 {
            println!("n={:?}", n );
        }
    
        n += 1 ;
    }
}
```

------
# For Loop







