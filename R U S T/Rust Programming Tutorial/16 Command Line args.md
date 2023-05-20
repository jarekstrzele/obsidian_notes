[[_ Rust Programming Tutorial]]

```rust
use std::env ;

fn main() {
	let args: Vec<String> = env::args().collect();
	for arg in args.iter(){
		println!("{}", arg) ;
	}
}

-----
$ cargo run 
--> output:
	target/debug/command_lind_args

$ cargo run arg1 arg2 
--> output:
	target/debug/command_lind_args
	arg1
	arg2

```










