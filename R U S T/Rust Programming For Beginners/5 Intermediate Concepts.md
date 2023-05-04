

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




