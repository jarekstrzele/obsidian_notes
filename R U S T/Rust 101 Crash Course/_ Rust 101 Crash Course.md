#rust #youtube #zero_to_master

https://www.youtube.com/watch?v=lzKeecy4OmQ


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




