[[_ Rust Build with GPT-4]]

#rust/type 

int, float, char, bool, fixed-size arrays, tuples -> on stack
`Vec<T>` resizable arrays on Heap
`String` on Heap
&T, &mut T references on Stack
&str immutable string references on (depends)
`Enum`, `Struct` on (depends)

# Stack vs Heap - memory management

## stack
>[!definition] STACK
> It stores stack frames

 You start a program and it will get a fixed size memory for stack (e.g. to allocate memory for variables)

![[stack_rust.excalidraw]]


## Heap
![[heap_rust_stack.excalidraw | 700]]





`let x: u8 =40 ;` on the stack

`let arr: Vec<u8> = vec![1,2,3,4,5] ;` on the heap
`arr.push(10)`

`arr_2` is the reference of `arr`
`let arr_3 = &arr[0..3] ;` (1,2,3) , the reference on the Stack pointing to a value on the Heap


`let mut s:String = String::from("Shai hountng") ;`  on the heap
`s.push(' ') ;`

`let s_2 = &s[1..3] ;` the reference on the stack pointing to a value on the Heap

`const MY_INT = 10 ;`  == `static MY_INT = 10 ;` it can't be mutable `const mut` generates an error

-----------
## String Literals and Static (Read-Only) Memory

> [!definition] static memory
> it is read only memory where this is actually known at compile time

```rust

fn main() {
 
  let s: String = String::from("hello string") ;
  let s_2: &str = &s[0..5] ;
  println!("{}", s_2) ;
  
  let msg: &str = "hello_msg" ; //msg is pointing to a location in memory (static memory
  println!("{}", msg) ;
let msg_string: String = "hello3".to_string();
println!("{}", msg_string)
  
    
}
```


--------
# Ownership and Borrowing - immutable references

#rust/ownership #rust/borrowing 


>[!definition] ownership
>- each value in Rust has single owner(i.e. variable) at a time
>- the value is dropped when its owner goes out of scope


>[!definition] borrowing
>- you can have any number of immutable (read-only) references
>- references must be valid


```rust

fn main() {
 
 // works
 let x: i32 = 50 ;
 let y: i32 = x ;
 println!("{}", x) ;
 println!("{}", y) ;
 
 
//  let s: String = String::from("hello") ;
//  let t: String = s ;
//  // println!("{}", s) ; // will not work, because `t` is a new owner
//  println!("{}", t) ;
    
  let s: String = String::from("hello") ;
  let t: String = s.clone() ; //deep copy, it is not recommended
  println!("{}", s) ; // it works
  println!("{}", t) ;
  
  
  // borrowing it, we point to it, we create this reference  
  // reference == borrowing
  let s: String = String::from("hello2") ;
  let t: &String = &s ; // `t` borrows the value of `s`
  let t2: &String = &s ; // `t` borrows the value of `s`
  let t3: &String = &s ; // `t` borrows the value of `s`
  println!("{}", s) ; 
  println!("{}", t) ;
    
}
```


```rust

fn make_string_dangle() -> &String{
    // `s` is an owner and when the fn is executed `s` will be dropped
    let s: String = String::from("dangle") ;
    let r: &String = &s ;
    r
}


fn main() {
 
    // not work
   let r: &String =  make_string_dangle() ;
   println!("{}", r) ;
}
```


It works
```rust

fn make_string_dangle() -> String{
    let s: String = String::from("dangle") ;
    
    s
}


fn main() {
 
    // not work
   let r: String =  make_string_dangle() ;
   println!("{}", r) ;
}
```



## Mutable references
```rust

fn main() {
 
 let mut s: String = String::from("does not work"); // mutable `s`
 let t: &String = &s; //immutable borrow
 s.push('?');
 println!("{}", t);
    
}
```


```rust


fn main() {
 
 let mut s: String = String::from("it works!"); // mutable `s`
 let t: &mut String = &mut s; //immutable borrow
 s.push('?');
 println!("{}", s);
    
}
```

```rust

fn change_string(text: &mut String){
    text.push('?');
}

fn main() {
 
 let mut s: String = String::from("it works!"); // mutable `s`
 let t: &mut String = &mut s; //immutable borrow
 change_string(t) ;
 println!("{}", s);
    
}

```























