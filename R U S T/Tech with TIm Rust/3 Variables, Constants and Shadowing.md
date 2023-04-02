	
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

## shadowing
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
	x is: 2 // this is from the other scope
	x is: 9
```

```rust
fn main(){
    let x = 4 ; 
        println!("x is: {}", x) ;
    // shadow: the same name other scope
    {
        let x = x - 2 ; 
        println!("x is: {}" , x) ;    
    }
   
    let x = x + 5 ; 
    println!("x is: {}" , x) ;

}


x is: 4
x is: 2
x is: 9
```


```rust
fn main(){
	let mut x = 4 ;
	x = "hello" ;
} // --> error, you can't change the type
```

```rust
fn main(){
	let x = 4;
	let x = "hello" ; // ok, you write a new variable x
}
```


# CONSTANT

Its type and value can't change

```rust

fn main(){
   const SECAONDS_IN_MINUTES: u32 = 60 ;
   println!("{} ", SECAONDS_IN_MINUTES) ;  

}
```
you have to write a type and value of `const`



