#rust/enum 
[[_ LetsGetRusty Ultimate Rust Lang Tutorial]]

```rust
enum IpAddrKind {
  // 4(String),
  V4(u8, u8, u8, u8),
  V6(String),
}

struct IpAddr {
  kind: IpAddrKind,
  address: String,
}


fn main(){
  // let localhost: IpAddrKind = IpAddrKind::V4(String::from("127.0.0.1")) ;
  let localhost: IpAddrKind = IpAddrKind::V4(127,0,0,1) ;
  
}
```





