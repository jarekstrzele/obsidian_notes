#rust/file
[[_ Rust Programming Tutorial]]


---
[[#generally]]
[[#Open a file]]
[[#Write to a file]]
[[#Multiple Source Files (Modules)]]







----

# generally
```rust
use std::fs::File ; 
use std::io::prelude::* ;
```

> This code consists of instructions importing Rust's standard library: `std::fs::File` and `std::io::prelude::*`.
> `std::fs::File` enables file operations such as creating, reading, writing, and deleting files.
> `std::io::prelude::*` contains basic types and structures, such as `Read` and `Write`, that are used in input/output (I/O) operations.
> The `use` statement allows using these libraries without the need to specify their full names every time they are used. For example, instead of writing `std::fs::File::open("file.txt")`, you can simply write `File::open("file.txt")` after importing `std::fs::File`.


> In Rust, `::` is used to access items (functions, types, constants, etc.) that are defined in a module or namespace. It is used to separate the module name or namespace from the item name.

> For example, if we want to access a function named `foo()` that is defined in the `my_module` module, we would use `my_module::foo()`.

> Similarly, if we want to access a constant named `PI` that is defined in the `std::f64` namespace, we would use `std::f64::PI`.

> The `::` operator can also be used in conjunction with type aliases or associated types to refer to types that are associated with a particular trait or structure. For example, if a trait defines an associated type named `Output`, we can refer to it as `TraitName::Output`.


-----
# Open a file
```rust
use std::fs::File ;
use std::io::prelude::* ;

fn main() {

	let mut file = File::open("info.txt").expect("Cant' opent file!") ;
	let mut contents = String::new();
	
	file.read_to_string(&mut contents)
		.expect("Oops! Can not reat the file...") ;
	
	  
	
	println!("File Contetns:\n\n{}", contents) ;
}
```

---
# Write to a file

```rust
use std::fs::File ;
use std::io::prelude::* ;


fn main() {
	let mut file = File::create("ouput.txt")
		.expect("Could not create file!") ;
	
	file.write_all(b"Welcome to dcode")
		.expect("Cannot write to the file!") ;

 }
```



------
# Multiple Source Files (Modules)
#rust/module

### By default functions in modules are **private**

main.rs
```rust
mod first_mod;

fn main() {
	first_mod::print_msg();
}
```

first_mod.rs
```rust
pub fn print_msg() {
	println!("How is going? print_msg public function")
}

fn print_msg_2() {
	println!("How is going? print_msg PRIVATE (access only in that file) function")
}
```



new project
```rust
// mod - key word to define your own module
mod decode {
	//private function
	fn foo_priv(){
		println!("I am a private fn") ;
	}

	//public function
	fn foo_pub(){
		foo_priv();
		println!("I am a public fn")
	}

	// nested module
	pub mod water{
		pub fn print_msg(){
			println!("I am a water") ;
		}
	}

}

fn main() {
	decode::foo_pub() ;
	decode::water::print_msg() ;
}
```


[]
