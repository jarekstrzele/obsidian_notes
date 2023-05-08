[[_ Rust Programming for Beginners]]


# Drive Macro for printing info
#rust/copy  #rust/clone   #rust/derive 

>[!info] Derive
>It is a special macrto that is applied to `enum` and `struct`
>`#[dervie(...)]` 
>`Debug` debug printing functionaity 
>`Clone`
>`Copy`  copies the argument, so ownership is not move from `struct` or `enum`


```rust
#[derive(Debug, Clone, Copy)]
enum Position {
  Manager,
  Supervisor,
  Worker,
}

#[derive(Debug, Clone, Copy)]
struct Employee {
  position: Position,
  work_hours: i64,
}

fn print_emp(emp: Employee) {
  println!("{:?}", emp) ;
}

fn main() {
  let me = Employee {
    position: Position::Worker,
    work_hours: 40,
  };

  println!("{:?}", me) ;
  println!("{:?}", me.position) ;
  print_emp(me);
  print_emp(me);
}
```


#rust/traits 
>In Rust, `Clone` and `Copy` are traits used for creating copies of values, but they have different purposes and behaviors.

> The `Copy` trait is used for types that are trivially copyable, meaning that when a value of that type is assigned to another variable or passed to a function, a bit-for-bit copy of the value is made. This means that the original value is not affected by changes made to the copied value, and the two values can be used independently. Types that implement `Copy` include `bool`, `char`, numeric types (`i32`, `f64`, etc.), and tuples containing types that implement `Copy`.

> On the other hand, the `Clone` trait is used for types that need a deep copy, meaning that a new object with the same data is created. This is typically used for types that own heap-allocated memory, such as `String` and `Vec<T>`. When a value of a type that implements `Clone` is assigned to another variable or passed to a function, a new copy of the value is created, and changes made to the copied value do not affect the original value.

> It's worth noting that not all types can implement both traits - some types cannot be trivially copied, and some cannot be cloned due to ownership and borrowing rules. It's also worth noting that `Copy` and `Clone` are both marker traits, meaning that they don't define any methods themselves, but rather signal to the compiler how the type should be treated.



-------
# Type Annotations
- required for functions signatures
- types are usually inferred
- can also be specified in code (expliciti type annotations)

```rust
// this type annotations  is required
fn print_many (msg: &str, count: i32) {}

// it is optional
let num: i32 = 15 ;
let a: char = 'a' ;
let left_click: Mouse = Mouse::LeftClick ;

```

## generics
```rust
// type annotation is optional
let nums: Vec<i32> = vec![1,2,3] ;
let letters: Vec<char> = vec!['a','b','c'] ;
let clicks: Vec<Mouse> = vec![
	Mouse::LeftClick,
	Mouse::RightClick,
	Mouse::UpClick,
	
]
```

------
# Enum
#rust/enum 
[[4 Data]]














