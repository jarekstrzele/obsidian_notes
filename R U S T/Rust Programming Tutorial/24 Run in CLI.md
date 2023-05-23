#rust/cli
[[_ Rust Programming Tutorial]]



`my_python_code.py`
```python
print("I am from Python")
```

```rust
use std::process::Command ;

fn main() {
	//python3 my_python_code.py
	let mut cmd = Command::new("python3") ; //create command `python3`
	cmd.arg("my_python_code.py") ; // add arg to `python3`

	//execute the command
	match cmd.output() {
		Ok(o) => {
			// unsafe because it doesn't check if input is utf8
			unsafe{
				println!("Output: {}", String::from_utf8_unchecked(o.stdout) );
		}
	},
	Err(e) => {
		println!("There was an error! {}" ,e) ;
		}
	}
}
```