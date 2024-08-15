#rust  

# hello world
```rust
// &'static is a "lifetime specifier", something you'll learn more about later
pub fn hello() -> &'static str {
    "Hello, World!"
}

fn main(){
    println!("{}", hello()) ;
}
```


# reverse string

>[!important] iterator znaków
>- to obiekt, który pozwala przechodzić (iterować) przez ciąg znaków (*String*, *&str*) jeden po drugi,
>- w Rust to efektywny i idiomatyczny sposób na przetwarzanie danych

```rust
let s = "example" ;
let mut iter = s.chars() ; // zwraca iterator znaków

//iter.next() zwraca kolejną wartość iteratora
while let Some(c) = iter.next(){
	println!("{}", c) ;
}
```
>

```rust
pub fn reverse(input: &str) -> String {
    
    input.chars().rev().collect()
}
```



















