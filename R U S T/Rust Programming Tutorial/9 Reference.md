#rust 

>[!info] reference
>It is just another way to refer to a variable


`&x` means you want to get a reference to the variable to `x`
```rust
fn main(){
	let mut x = 10;
	// let x = 10 ; it will be ok
	let xr = &x;
	let dom = &x;

	println!("x is {}", xr) ; // output `x is 10`
	println!("x is {}", dom) ; // output `x is 10`
	println!("x is {}", x) ; // output `x is 10`
}
```
we can use `xr` in the same way we use `x`

## you want to change the value of `x`;
```rust
fn main(){
  let mut x = 10;
  let xr = &x;

  xr += 1; // error, you have to use mutable reference
 
  println!("x is {}", xr) ;
  
}
```

```rust
fn main(){
  let mut x = 10;
  let xr = &mut x;

  *xr += 1; // ok
 
  println!("x is {}", xr) ;
  
}

output
x is 11
```


but if you want to display `x`, you will get an error
```rust
fn main(){
  let mut x = 10;
  let xr = &mut x;

  *xr += 1; // everything is ok
 
  println!("x is {}", x) ;
  
}

```

but in older version you can't have to mutable references, so you should wrap you code in black like this

```rust

fn main(){
  let mut x = 10;
  {
    let xr = &mut x;
    *xr += 1; // error, you have to use mutable reference
  }
  println!("x is {}", x) ;
  
```






