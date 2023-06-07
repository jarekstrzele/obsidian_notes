[[_ Ultimate Rust Crash Course]]


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

`let s2=s1 ;` you move the ownership for `s1` to `s2` (it can be only one owner)
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
do_stuff(s1) ;

fn do_stuff(s: &String) {

}
```

`&String` -- it indicates a reference to a type







---
# References and Borrowing




















