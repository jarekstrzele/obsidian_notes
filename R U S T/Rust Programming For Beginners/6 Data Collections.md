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


















