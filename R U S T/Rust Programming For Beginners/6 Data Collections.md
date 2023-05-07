[[_ Rust Programming for Beginners]]

# Vectors
#rust/vector 

>[!info] Vector
>- multiple pieces od data (must be the same type)
>- used for lists of information
>- can add, remove, and traverse the entires

```rust
let my_nums = vec![1,2,3] ;
let mut my_nums2 = Vec::new();

my_nums.push(1) ; // add new item to the vector
my_nums.pop() ; 
my_nums.lent() ;

let two = my_nums[1] ; //slice notation, `1` it is an index

let my_num3 = vec![1,2,3] ;

for num in my_num3 {
  println!("{:?}", num) ;
}

```
>
```rust
struct Test {
  score: i32
}

fn main(){
  let my_score = vec![
    Test { score: 90},
    Test { score: 88},
    Test { score: 77},
    Test { score: 93},
    Test { score: 12},
    Test { score: 50},
  ] ;

  for t in my_score {
    println!("score = {:?}", t.score) ;
  }
}

output
score = 90
score = 88
score = 77
score = 93
score = 12
score = 50
 
```


```rust
fn main(){
  let nums = vec![10,20,30,40] ;

  // for n in nums {
    for n in &nums {  
  // if n == 30{
    //   println!("thirty");
    // } else {
    //   println!("{:?}", n) ;
    // }
    match n {
      30 => println!("thirty") ,
      _ => println!("{:?}", n)
    }
  }

  println!("number of elements = {:?}", nums.len()) ;
}


output
10
20
thirty
40
number of elements = 4
```


--------
# String
>[!info] String
>- there are many types of string in Rust
>- two commonly used types of strings:
>	- `String` - owned
>	- `&str` - borrowed `String` slice
>- Must use an owned `String` to store in a `struct`
>- Use `&str` when passing to a function

```rust

fn print_it(data: &str){
	println!("{:?}", data) ;
}

fn main(){
	print_it("a string slice") ; // "a string slice" - it is automatically borrowed
  let owned_string = "owned string".to_owned() ; //string_slice -> to_owned() -> a own string
  let another_owned = String::from("another") ;
  print_it(&owned_string) ; //borrowed own string
  print_it(&another_owned) ; // borrowed own string
  
  
}
```

```rust
struct Employee {
  // name: &str, // you can not store a string slice in this manner, because that structuter won't be responsible to delete the string
  name: String
}

fn main(){
	//let emp_name = "Jayson" ; // "Jayson" will be automatically borrowd
  let emp_name = "Jayson".to_owned() ;
  // or instead of using `to_own()` you can write:
  let emp_name = String::from("Jayson") ;
  let emp = Employee { name: emp_name } ;
}
```


>[!info] String -recap
>- Strings are automatically borrowed 
>- Use `.to_own()` or `String::from()` to create an owned copy of a string slice
>- use an owned `String` when storing in a `struct`



















