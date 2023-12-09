
>[!inf] RULES
>- a package must have at least one crate
>- a package could have either zero library crates or one library crate  
>- a package could have any number of binary crates `src/bin`



# Package
`cargo new projectName` --> generates a package
in `Cargo.toml` you will find 
```toml
[package]
name = ""
version =
authors = 
edition


```

# PATHs

### `cargo new --lib projectName`
- structure is the same
- instead of `main.rs` you have `lib.rs`> `test module`
e.g. -> `lib.rs`
```rust
mod front_of_house {
	pub mod hosting {
		pub fn add_to_waitlist() {}
		fn seat_at_table() {}
	}

	pub fn eat_at_restaurant(){
	// Absolute path
		

	mod serving {
		fn take_order() {}
		fn serv_order() {}
		fn take_payment() {}
	}
}

crate:front_of_house::hosting::add_to__waitlist();

	// relative path
	front_of_house::hosting::add_to_waitlist();
}
```

## MODULE TREE
```
crate 
	|---front_of_house
	|	|--hosting
	|		|--add_to_waitlist
	|		|--seat_at_table
	|
	|---serving
		|-- take_order
		|-- serve_order
		|-- take_payment

```
that `crate` is a module that gets created by default for our crate root which is `lib.rs`

relative paths start from the current module

### `super`
```rust
fn serve_order(){}

mod back_of_house {
	fn fix_incorrect_order(){
		cook_order():
		super::serve_order();
	}

	fn cook_order() {}
	
}
```

>[!important] Privacy rules
>
> - all items are private by default  (e.g. struct, fn, enum, mod, ...)
> - even `stuct` is public, its, fields are private by default
> - event in the `struct` is one private field, you can't create an instance of that structure directly
> - `enum` - if it is `pub`  all its variants are public too, so you cannot mark its variants as `pub`
--------
# Crates
a new package stores **crates**
Crates can be:
- ==binary crates==, so you can execute it
- ==library crates== which is code that can be used by other programs

Crates contain modules.

**a crate root** (e.g. `main.rs`) is the source file that the rust compiler starts at when building your crate

**library** (`src/lib.rs`)
if `lib.rs` defied in the root of your source directory then rust will automatically create a library crate with the same name as your package and `lib.rs` will be the create root 

Your `.toml` file may have no annotation, but you have two crates `main.rs`, `lib.rs`



# Modules
They allow you to organize a chunk of code and control the privacy rules


# Workspace
They contain packages


# `use` keyword
#rust/use

instead of using long path (e.g. `front_of_house::hosting::add_to_waitlist()` you can use `use`)

```rust
mod front_of_house {
	pub mod hosting {
		pub fn add_to_waitlist() {}
	}
}

use crate::front_of_house::hosting ;

pub fn eat_at_restaurant(){
	//font_of_house::hosting:add_to_waitlist();
	hosting::add_to_waitlist() ;
}
```


### renaming import
```rust
use std::fmt::Result ;
use std::io::Result as IoResult ;

fn fun2() -> IoResult<()> {

	Ok(())
}
```

### external importing
```rust
use rand::{Rng, CryptoRng, ErrorKind::Transient} ;

use std::io;
use std::io::Write ;
//you can write equivalent:
use std::io::{self, Write} ;
```

``
import all
`use std::io::* ;`







