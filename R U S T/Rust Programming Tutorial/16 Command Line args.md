[[_ Rust Programming Tutorial]]

```rust
use std::env ;

fn main() {
	let args: Vec<String> = env::args().collect();
	for arg in args.iter(){
		println!("{}", arg) ;
	}
}
```










