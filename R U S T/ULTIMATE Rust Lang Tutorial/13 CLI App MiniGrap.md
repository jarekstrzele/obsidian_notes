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

---
create a file `poem.txt` with some text
`main.rs`
```rust
use std::env;
use std::fs;

fn main() {
	let args: Vec<String> = env::args().collect() ;
	let query = &args[1] ;
	let filename = &args[2] ;

	println!("Searching for {}", query) ;
	println!("in file {}", filename) ;

	let contents = fs::read_to_string(filename).expect("Something went wrong reading the file") ;
	println!("With text: \n{}", contents) ;
}
```


## refactoring

### too many responsibilities in the main file
first version
```rust
use std::env;
use std::fs;

fn main() {
	let args: Vec<String> = env::args().collect() ;
	let config = Config::new(&args) ;
		  
	println!("Searching for {}", config.query) ;
	println!("in file {}", config.filename) ;

	let contents = fs::read_to_string(config.filename).expect("Something went wrong reading the file") ;
	println!("With text: \n{}", contents) ;
}

// to link query with filename
struct Config{
	query: String,
	filename: String,
}

impl Config {
	fn new(args: &[String]) -> Config {
		if args.len() < 3 {
			panic!("not enough arguments") ;
		}
		let query = args[1].clone() ;
		let filename = args[2].clone() ;

	Config { query, filename }
	}
}
```

better way to handle errors




