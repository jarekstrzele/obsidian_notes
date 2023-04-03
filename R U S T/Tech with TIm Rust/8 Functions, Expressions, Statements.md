#rust/function #rust/expression #rust/statement
[[_ Rust Tech with Tim]]

# Functions
```rust

fn main(){
    test_one() ;
    test_one() ;
}


fn test_one(){
    println!("Test has been called...")
}
```
the placement of the function definition has no matter


```rust

fn main(){
    add_nums(10,20); 
}


fn add_nums(x: i32, y: i32){
    println!("the sum is: {} ", x + y) ;
}
```


# Expressions
==Rust function can return an expression but cannot return a statement !!!!!!==

### statement
It is going to be something like:
- a variable declaration 	-> `let x = 20;` it doesn't evaluate anything
- 


