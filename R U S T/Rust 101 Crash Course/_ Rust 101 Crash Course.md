#rust #youtube #zero_to_master
https://www.youtube.com/watch?v=lzKeecy4OmQ

------------
[[1 Data types]]
[[2 Expressions]]
[[3 Memory]]
[[4 Vectors - data structure]]
[[5 String]]


------------

# In this note:

[[#Tools]]
[[#Comments]]
[[#Data types]]
[[#Variable]]
[[#Functions]]
[[#Println macro]]
[[#Control flow `if`]]
[[#loops]]
[[#Match]]



----
# Tools
- rustup ( manages Rust installation)
- VS Code
- MSVC C++ Build Tools (needed to build on Windows)
	- check MSVC 
	- check Windows 10 SDK

### `cargo init projectName`
### `cargo run`

----
# Comments
`// one line comment`





-----
# Data types
- memory only stores binary data
	- anything can be represented in binary
- program determines what the binary represents
- basic types that are universally useful are provided by the language
		`bool, integer, double, character, string`
`a` char
"a" string


---
# Variable
#rust/variable
- a variable is to assign data to a temporary memory location (allows programmer to easily work with memory)
- can be set to any value & type
- immutable y default, but can be mutable
```rust
let two = 2 ;
let he = "hello" ;
let mut my_name = "bill" ;
let your_name = my_name ;
```

-------
# Functions
#rust/function 

- a way to encapsulate program functionality
- optionally accept data
- optionally return data
- utilized for code organization (also makes code easier to read)

```rust
fn add(a: i32, b: i32) -> i32 {
	a + b
}
```

----

# Println macro
- macros expand into additional code
- `println` prints information to the terminal
- 
```rust
let life = 42 ;
println("www") ;
println("{:?}", life) ;

```
`:}` debug print
`?` place for data 

```rust
let life = 42 ;
println!("{life:?}") ;
println!("{life}") ;

```

---
# Control flow `if`
`if, else, ` `else if`
always us `else`

-----
# Loops

`loop` infinite loop
`while` conditional loop

```rust
let mut a = 0;
loop {
	if a == 5 {
		break ;
	}
	println!("{:?}", a);
	a = a + 1 ;
}
```


```rust
let mut a = 0 ;
while a != 5 {
	println!("{:?}", a) ;
	a = a + 1 ;
}
```

------

# Basic arithmetic
```rust
fn sub(a: i32, b: i32) -> i32 {
	a - b
}

fn main(){
	let sum = 2 + 2;
	let value = 10 - 5;
	let division = 10 / 2 ;
	let mult = 5 * 5 ;

	let rem = 6 % 2;
}




```


 ----------
# Match
#rust/match 

==Match must be exhaustive==

```rust
fn main() {
	let some_bool = true ;
	match some_bool {
		true => println!("it's true"),
		false => println!("it's false"),
	}
}
```

#### `_` all posibility



```rust
enum Discount {
	Percent(i32),
	Flat(i32),
}

struct Ticker{
	event: String,
	price: i32,
}

fn main(){
	let n = 3;
	match n {
		3 => println!("three"),
		other => println!("number: {:?}", other),
	}

	let flat = Discount::Flat(2) ;
	match flat {
		Discount::Flat(2) => println!("flat discount of {:?}", 2),
		Discount::Flat(amount) => println!("flat discount of {:?}", amount),
		_ => (),
	}

let concert = Ticker {
	event: "concert".to_owned(),
	price: 50,
};

// .. - this means ignore others fields
match concert {
	Ticker { price: 50, event} => println!("event @ 50 = {:?}", event),
	Ticker {price, ..} => println!("price= {:?}", price),
	}
}
```












