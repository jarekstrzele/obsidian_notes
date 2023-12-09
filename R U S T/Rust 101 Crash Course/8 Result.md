#rust/result 

- a data type that contains one of two types of data:
	- "Successful" data
	- "Error" data
- Used in scenarios where an action needs to be taken, but has the possibility of failure 
	- copying a file
	- connecting to a website

DEFINITION
```rust
enum Result<T,E>{
	Ok(T),
	Err(E),
}
```


Example
```rust
fn get_sound(name: &str) -> Result<SoundData, String> {
	if name=="alert" {
		Ok(SoundData::new("alert")),
	} else {
		Err("unable to find sound data".to_owned())
	}
}

let sound = get_sound("alert") ;
match sound {
	Ok(_)=>println!("sound data located"),
	Err(e) => println!("error: {:?}", e),
}

```

### `?` automatically perform a `match` operation:
- if Ok(), inner data will get out
- if Err(), error will be display




