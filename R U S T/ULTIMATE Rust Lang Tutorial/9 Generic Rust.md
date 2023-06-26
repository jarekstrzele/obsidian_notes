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

# generic struct

```
```







