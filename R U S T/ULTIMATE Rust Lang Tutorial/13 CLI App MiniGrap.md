[[_ LetsGetRusty Ultimate Rust Lang Tutorial]]

`use std:env` - a user will be able to pass in a string and a file name

`collect()` - initializes a vector, makes a vector from args passed at invocation
`env::args()` - returns an iterator that allows iterating over the command-line arguments
`env::args().collect()` - it collects the command-line args and put them into the vector

```rust
use std::env;

fn main() {
	let args: Vec<String> = env::args().collect() ;
	println!("{:?}", args) ;
}
```

`cargo run`  -> `["target/debug/minigrep"]` a path to our binary
```bash
$ cargo run first dua
    Finished dev [unoptimized + debuginfo] target(s) in 0.00s
     Running `target/debug/minigrep first dua`
["target/debug/minigrep", "first", "dua"]
```




