#rust/memory 



# Offset

>[!info] memory
> - memory is stored using binary `0`, `1`
> - computer optimized for bytes *1 byte == 8 contiguous bits*
> - fully contiguous

>[!info] addresses
>- all data in memory has an "address"
>	- used to locate data
>	- always the same - only data changes
>- usually don't utilize addresses directly
>	- variables handle most of the work

>[!info] offsets
>- items can be located at an address using an "offset",
>- offsets begin at `0`
>- represent the number of bytes away from the original address (normally deal with indexes instead)

![[rust_address_offset.excalidraw | 600]]


# Managing memory

#rust/borrowing 

## borrowing
- programs must track memory
	- if they fail to do so, a "leak" occurs
- Rust utilizes an "ownership" model to manage memory
	- the "owner" of memory is responsible for cleaning yp the memory
- memory can either be "==moved==" of "==borrowed=="

### moved
```rust
enum Light {
	Bright,
	Dull,
}

fn display_light(light: Light){
	match light{
		Light::Bright => println!("Bright"),
		Light::Dull => println!("dull"),
	}
} // when the function is finshed, the dull is deleted

fn main(){
	let dull = Light::Dull; // the owner of dull is the main function
	display_light(dull) ; // the ownership is MOVED to display_light function
	display_light(dull) ; // error
}


```


### borrowed `&`
```rust
enum Light {
	Bright,
	Dull,
}

fn display_light(light: &Light){
	match light{
		Light::Bright => println!("Bright"),
		Light::Dull => println!("dull"),
	}
} // when the function is finshed, the dull is deleted

fn main(){
	let dull = Light::Dull; // the owner of dull is the main function
	display_light(&dull) ; // the function only borrows the dull (it passes reference)
	display_light(&dull) ; // O K 
}


```








