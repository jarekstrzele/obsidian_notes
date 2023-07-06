#rust/generics 


# Generic Functions
```rust


// fn get_largest(number_list: &[i32]) -> i32{
//   let mut largest: i32 = number_list[0] ;
//   for &number in number_list {
//     if number > largest{
//       largest = number ;
//     }
//   }
//   largest
// }

// generic
// because you use `>` you have to make some restrictions
// PartialOrd
fn get_largest<T: PartialOrd + Copy>(number_list: &[T]) -> T{
  let mut largest: T = number_list[0] ;
  for &number in number_list {
    if number > largest{
      largest = number ;
    }
  }
  largest
}


fn main(){
  let num_list = vec![102,34,6000,89,54,2,43,8] ;
  let max: i32 = get_largest(&num_list) ;
  println!("max = {} ", max) ;
  // println!("num_list = {:?} ", num_list) ;
}

```

# generic `struct`

```rust
struct Point<T, U>{
  x: T,
  y: U,
}

fn main(){
  let p1 = Point {x:5, y:10} ;
  let p2 = Point {x:5.0, y: 10.11} ;
  let p3 = Point {x: 4, y: 12.45} ;
}
```

```rust
struct Point<T, U>{
  x: T,
  y: U,
}

impl<T,U> Point<T,U>{
  fn mixup<V,W>(self, other: Point<V,W>) -> Point<T,W>{
    Point {
      x: self.x,
      y: other.y,
    }
  }
}

fn main(){
  let p1 = Point {x:5, y:10.4} ;
  let p2 = Point {x:"Hello", y: 'c'} ;
  let p3 = p1.mixup(p2);
  println!("p3.x = {}, p3.y = {}", p3.x, p3.y) ;
}
```






# generic `enum`
```rust
enum Option<t>{
	Some(T),
	None
}

enum Result<T,E>{
	Ok(T),
	Err(E),
}
```








