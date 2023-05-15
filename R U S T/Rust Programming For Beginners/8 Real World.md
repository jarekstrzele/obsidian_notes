

# User Input
- `io` module has its own `Err` type, so
- you don't need to write your own,
- `Err` is automatically provided

>[!info] Buffer
>It is just some space set aside that some othe functionality can use and operate with

```rust
fn get_input() -> io::Result<String> {
	let mut buffer = String::new(); // string buffer
	io::stdin().read_line(&mut buffer)? ;
	Ok() ;
}
```
 reads one line of the input from the standard input and save that line into the butter that is borrowing in mutable wau
#rust/borrowing 
*a mutable borrow* 
- the initial variable must be mutable
- the function that accepts the mutable borrow must also be specified in their function signature
- so the function will be able to acces this buffer in a mutable fushion and CHANGE THE CONTENTS of this BUFFER
- `?` this function may possible fail
	- if this fails, we will return an error from the function and the data will not have been read from the terminal
	- if the data is read properly, hten it will be automatically available within our buffer, we return `Ok(buffer)`, because we return a `Result`
	- `Ok(buffer.trim().to_owned())` you also need t take ownership of the buffer again, because when we do trim , it just creates a slice, because the data is all there and it only needs to return the data that is not empy spaces (`-> Result<String>` not `-> Resutl<&str>`)














