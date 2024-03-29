[[_ Ultimate Rust Crash Course 1]]


# Ownership

### THREE RULES:
1. Each value has an owner.
2. Only one owner. (no variables may share ownership, other variables can borrow ownership)
3. Value gets dropped if its owner goes out of the scope

```rust
let s1 = String::from("abc") ;
le s2 = s1 ; // the value of s1 is MOVED to s2, because only one variable can own the value
println!("{}", s1) ; // Error!!!
```

S T A C K   | H E A P   
--- | ---
In order   |   Unordered
Fixed-size | Variable-size
LIFO | Unordered
Fast |Slow

so
`let s1 = String::from("abc") ;` 
`s1` on the Stack:
- `ptr` --the pointer to--> `a` that is on the heap (on the heap there are `a`, `b`, `c`)
- `len` : 3
- `capacity`: 3

`let s2=s1 ;` you move the ownership from `s1` to `s2` (it can be only one owner)
so
`s2` on the Stack:
- `ptr` -- the pointer to --> the same `a` that is on the heap
- `len` : 3
- `capacity`: 3
and `s1` is uninitialized and the compiler won't let you use it

to **copy** a value use `clone()` method:
```rust
let s1 = String::from("abc") ;
let s2 = s1.clone() ;
println("{}", s1) ;
```

`clone()` : (*deep copy* in other languages)
#rust/clone
- it copies the stack
- it copies the heap
- so there will be two pointers on the Stack and two strings "abc" on the Heap
- so all three principles are satisfied: 
	- 1. the value has to have an owner
	- 2. only one owner
	- 3. the variable out of the scope the value will be immediately dropped -DROP:
		- destructor
		- free heap
		- pop stack
		- so ==> ==no leaks, no dangling pointers==

#rust.copy
`copy()` when only the Stack data is being copied

-------
# References and Borrowing

```rust
let s1 = String::from("abc") ;
do_stuff(s1) ;

fn do_stuff(s: String) {

}
```
in this code we pass `s1` to that function, `s1` is MOVED into the  local variable `s` in the function `do_stuff`
so 
we **can't use** `s1` anymore, because it got moved!!!!!

#rust/reference #rust/borrowing 
```rust
let s1 = String::from("abc") ;
do_stuff(&s1) ;

fn do_stuff(s: &String) {

}
```

`do_stuff(&s1)` 
	-  you pass a reference (`s1`  **retains** ownership of the value),
	-  **borrows** a reference to the value (THE REFERENCE, NOT THE VALUE,  **gets moved into** the function, so at the end of the scope the reference gets dropped)

`(s: &String)` -- it indicates a reference to a type

when we create  a reference to `s1`, Rust creates a pointer to `s1`

`s`  -- points to --> the pointer of `s1`  -- points to --> `a` on the Heap

### ==reference are immutable by default ==

if you *make*
- a  *mutable reference* (e.g. `&mut String`) 
- to a *mutable value* (`let mut s1...`) 
- that you can use the reference *to change the value* as well
```rust
let mut s1 = String::from("abc") ;
do_stuff(&mut s1) ;

fn do_stuff(s: &mut String){
	s.insert_str(0, "Hi, ") ;
}
```

#### `x` --this is a variable
#### `&x` this creates an immutable reference to that variable
#### `&mut x`  this creates a mutable reference to that variable's value
##### `s.insert_str()` ----> the dot operator for a method or a field **auto-dereferences** down to the actual value
if you want manually dereferenced `s`. it would look like this: `(*s).instert_str()`

`i32` this is a type of a value
`&i32` this is a immutable reference to that value
`&mut i32` this is a mutable reference to that value

```rust
x: &mut i32 // this is a mutable reference to a value
*x // deferencing `x` gives mutable access to the value
```

>[!important]
> ==you can have==:
> - exactly **ONE MUTABLE reference**  
> - **ANY NUMBER of IMMUTABLE references**
this rule applies across all threads!!


```rust
// Silence some warnings so they don't distract from the exercise.

#![allow(unused_mut, unused_variables)]
fn main() {
// This fancy stuff either gets the first argument as a String, or prints
// usage and exits if an argument was not supplied to the program.

	let mut arg: String = std::env::args().nth(1).unwrap_or_else(|| {

	println!("Please supply an argument to this program.");

	std::process::exit(-1);

});

// 1. Write a function `inspect` that takes a reference to a String, returns nothing, but
// prints whether the contents of the String is plural or singular. Then uncomment and run this
// code with `cargo run apple` and `cargo run apples'. Hint: use `.ends_with("s")` on the
// String reference

fn inspect(arg: &String){
	if arg.ends_with("s") {
		println!("plural") ;
	} else {
		println!("singular") ;
	}
}

inspect(&arg) ;

// 2. Write a function `change` that takes a *mutable* reference to a String and adds an "s" to
// the String if it doesn't already end with "s". Then uncomment and run the code below with
// `cargo run apple`. Hint: use `.push_str("s")` on the mutable String reference to add an "s".

fn change(arg: &mut String){
	if !arg.ends_with("s") {
		arg.push_str("s") ;
	}
}

change(&mut arg);
println!("I have many {}", arg);

// 3. Write a function `eat` that accepts ownership of (consumes) a String and returns a bool
// indicating whether or not the String both starts with a "b" AND contains an "a".
// Hint 1: use `.starts_with("b")` and `.contains("a")`
// Hint 2: `&&` is the boolean "AND" operator

fn eat(arg: String) -> bool{
	// if arg.starts_with("b") && arg.contains("a"){
		// true
	// } else {
		// false
	// }
//simplify

arg.starts_with("b") && arg.contains("a")
}

if eat(arg) {
	println!("Might be bananas");
} else {
	println!("Not bananas");
}

  

// Try running this program with "boat", "banana", and "grapes" as the arguments :-)
// Challenge: Write a function "bedazzle" that takes a mutable reference to a String and
// ignores what is in the string and replaces the contents of the string with the String
// "sparkly". Then uncomment the code below.
fn bedazzle(arg: &mut String){
	*arg = String::from("sparkly") ; //without '*' mismatched types expected `&mut String`, found `String`

}

// Hint: You will need to dereference the mutable reference in order to assign it a

// new value.

//

	let mut material = "mud".to_string();
	println!("This material is just `{}`.", material);
	bedazzle(&mut material);
	println!("Wow! Now the material is `{}`!", material);

}
```






