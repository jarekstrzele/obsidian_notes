#udemy #rust 
#lennon_jayson

in the terminal:
### `cargo run --bin projectName` 
- `bin` the binary is an executable program

### `cargo run -q --bin projectName`
`-q` without some messages in the terminal, only the result



--------------
[[2 Making Decisions]]
[[3 Repetition]]
[[4 Data]]
[[5 Intermediate Concepts]]
[[6 Data Collections]]
[[7 Advanced Concepts]]
[[8 Real World]]
[[9 Refining Your Code]]


---------
tools:
- rustup - manages rust installation
- VS Code
- MSVC C++ Build Tools (needed to build on WIndows)

# Data Types
>[!info] data types
>- memory only stores binary data (anything can be represented in binary)
>- program determines what the binary represents
>- basic types that are universally  usefull are provided by the language
>	- boolean: true, false
>	- integer
>	- double/float
>	- character 'A', 'b'
>	- string "hellow,", "string"


# Variable
> - assign data to a temporary memory location (allows programmer to easily work with memory)
> - can be set to any value & type
> - immutable: cannot b changed **by default**
> - mutable: can be changed


```rust
let two = 2 ;
let hello = "hello " ;
let j = 'j' ;
let mut my_name = "bill" ;
let quit_program = false ;
let your_hald = my_half;
```

---
# Function
>- a way to encapsulate program functionality
>- optionally accept data
>- optionally return data
>- utilized for code organization
>	- also makes code easier to read
>- can be executed by "calling" the function


```rust
fn add(a: i32, b: i32) -> i32 {
	a + b
}

let x = add(1,1);
let y = add (3,0);
let z = add(x,1) ;
```


--------
# Println `macro` 
"prints" display. information to the terminal

```rust
let life = 42;
println!("hello");
println!("{:?}, life") ; // :? - debug mode
println("{:?} {:?}", life, life) ;
```


------
# Loop

`loop` - infinite loop
`while` - conditional loop

```rust
let mut a = 0;
loop{
	if a == 5 {
		break ;
	}
	println!("{:?}", a) ;
	a = a + 1 ;
}
```


```rust
let mut a = 0 ;
while (a != 5){
	println!("{:?}", a) ;
	a = a + 1 ;
}
```

----
# First App
```rust

fn first_name(){
  println!("Jaro") ;
}

fn last_name(){
  println!("Strzele") ;
}

fn main() {
  first_name() ;
  last_name() ;
}
```











