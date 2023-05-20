#rust/file

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







