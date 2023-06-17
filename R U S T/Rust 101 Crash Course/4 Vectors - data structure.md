[[_ Rust 101 Crash Course]]
#rust/vector 

https://www.youtube.com/watch?v=lzKeecy4OmQ

>[!info] Vector
>Multiple pieces od data (==must be the same type==)
>used for lists of information
>can add, remove, travers the entries

```rust
let my_numbers = vec![1,2,3] ;

let mut my_numbers = Vec::new();
my_numbers.push(1);
my_numbers.push(2);
my_numbers.push(3);
my_numbers.pop(); //removes the last elem
my_numbers.net(); // this is 2

let two = my_numbers[1];


for num in my_numbers{
	println!("{:?}", num) ;
}
```










