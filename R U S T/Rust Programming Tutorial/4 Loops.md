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
```rust
fn main() {
    let nums = 10..33 ;
    
    for i in nums {
        println!("Nums: {}", i) ;
    }
}
```

with vector:
```rust
fn main() {
    let animals = vec!["rabbit" , "frog", "hors"] ;
    
    for a in animals.iter() {
        println!("Animals: {}", a) ;
    }

}
```


with value and index from vector:
```rust
fn main() {
    let animals = vec!["rabbit" , "frog", "hors"] ;
    
    for (index, animal) in animals.iter().enumerate() {
        println!("index ({}), animal ({})", index, animal) ;
    }

}

output:
index (0), animal (rabbit)
index (1), animal (frog)
index (2), animal (hors)
```

> `iter()` returns a references to the elements of the vector
> without `iter()` the elements of the vector are copied 








