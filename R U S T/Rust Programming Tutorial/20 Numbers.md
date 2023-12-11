#rust/number

https://www.youtube.com/watch?v=I5tKaSAcZRY&list=PLVvjrrRCBy2JSHf9tGxGKJ-bYAN_uDCUL&index=33

[[_ Rust Programming Tutorial]]


----
# Random nums
- you new to use external crates
- `Cargo.toml` > `dependecies` > add `rand = "0.8.0"`
- in the `main.rs` 

```rust
use rand::Rng;

fn main() {
	// tworzenie generatora liczb losowych
	let mut rng = rand::thread_rng() ;
	let random_number: u32 = rng.gen_range(1..=6);
	println!("Random Number 1-100: {}", random_number) ;
	let random_number: u32 = rng.gen_range(1..6);
	println!("Random Number 1-99: {}", random_number) ;

	// generate random boolean
	// flip a coin
	let random_bool: bool = rng.gen() ;
	println!("Random Number 1-99: {}", random_bool) ;
	// prawdopodobieństwo otrzymania prawdy
	let random_bool: bool = rng.gen_bool(0.7) ; // 70% for true, 30% for false
	println!("Random Number 1-99: {}", random_bool) ;
}
```



