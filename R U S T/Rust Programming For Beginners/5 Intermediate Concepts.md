[[#Expressions]]
[[#Memory]]
[[#Ownership]]


---
[[_ Rust Programming for Beginners]]

---
# Expressions
#rust/expression 
>- Rust is an expression-based language (most things are evaluated and return some value)
>- Expression values coalesce to a single point (can be used for nesting logic)

expression examples:
`if, match, >, ...`
```rust
let my_num = 3; 
let msg = match my_num{
   1 => "hello",
   _ => "goodbye"
}
```

```rust
enum Access {
  Admin,
  Manager,
  User,
  Guest
}
fn main(){

  //secret file: admins only
  let access_level = Access::User ;
  let can_access_file = match access_level{
    Access::Admin => true,
    _ => false
  } ;

println!("Can read a secret file? {:?}", can_access_file) ;
}
```


```rust
fn print_msg(gt_100: bool){
  match gt_100 {
    true => println!("It's big"),
    false => println!("It's small"),
  }
}

fn main(){
  let value = 100;
  let is_gt_100 = value > 100;
  print_msg(is_gt_100) ;
  
}

```


---
# Memory
#rust/memory 

>[!info] Memory
> - memory is stored using binary (bits: 0 or 1)
> - computer optimized for bytes (1 byte == 8 contiguous bits)
> -  all data in memory has an "address" 
> 	- used to locate data
> 	- always the same - only data changes
> - usually don't utilize address directly (variables handle most of the work)
>

>[!info] memory offsets (przesunięcia pamięci)
>	- item can be located at an address using an "offset"
>	- offsets begin at 0
>	- represent the number of bytes away from the orginal addres (normally deal with indexes instead)













-------------
# Ownership























