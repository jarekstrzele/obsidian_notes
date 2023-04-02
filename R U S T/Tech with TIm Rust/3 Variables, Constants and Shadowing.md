	
```rust
fn main(){
	let x = 4; // you can't change the variable type
			   // compiler set Int for x variable
	println!("x is: {}", x)
// by default all variable are immutable
	x = 5; // it generates an error
	println!("x is: {}" , x)

}
```


```rust
fn main(){
	let mut x = 4; 
		println!("x is: {}", x)
  // now x is mut-able
	x = 5; 
	println!("x is: {}" , x)

}
```

---------
```rust
fn main(){
    let x = 4 ; 
        println!("x is: {}", x) ;
    // now override the x
    let x = 5 ; // this is a new variable
    println!("x is: {}" , x) ;

}
	 x is: 4
	 x is: 5
```


---------
```rust
fn main(){
    let x = 4 ; 
        println!("x is: {}", x) ;
    // now override the x
    let x = 5 ; 
    println!("x is: {}" , x) ;
    let x = x + 5 ; 
    println!("x is: {}" , x) ;

}

	x is: 4
	x is: 5
	x is: 10
```

------------
```rust
fn main(){
    let x = 4 ; 
        println!("x is: {}", x) ;
    // shadow: the same name other scope
    {
        let x = 2 ; 
        println!("x is: {}" , x) ;    
    }
   
    let x = x + 5 ; 
    println!("x is: {}" , x) ;

}

	x is: 4
	x is: 2
	x is: 9
```


