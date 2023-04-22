https://www.youtube.com/watch?v=cH6Qv47MPwk
#rust.array
[[_ Rust Programming Tutorial]]


```rust
fn main(){
  let nums = [10,20,30,40] ; //in the background -> let nums: [i32; 5] = [10,20,30,40]

  println!("{}",nums[2]) ;

  for i in nums.iter(){
    println!("{} ", i) ;
  }
// 30
// 10 
// 20 
// 30 
// 40 

  
  // by index
  for i in 0..nums.len(){
    println!("index {}, element {} ", i,  nums[i]) ;
  }
  //index 0, element 10 
// index 1, element 20 
// index 2, element 30 
// index 3, element 40 

 let my_array = ['a';10] ;
  println!("{:?}", my_array) ;
  // ['a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a', 'a']
}

```



