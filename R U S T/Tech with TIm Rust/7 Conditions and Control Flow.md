https://www.youtube.com/watch?v=MOa7ulhNYc0&list=PLzMcBGfZo4-nyLTlSRBvo0zjSnCnqjHYQ&index=7

[[_ Rust Tech with Tim]]

`> , < , >= , <= , == , !=`

When you compare objects that are different types to each other you can run into error:
- ` 2 <= 2.2` --->  `(2 as f32) <= 2.2`


`&&` and
`||` or
`!` not

```rust
fn main(){
	let food= "cookie" ;

	if food == "cookie"{
		println!("I like cookies too")
	} else if food == "fruit"{
		println!("that sounds healthy")
	} else {
		println!("oh, that's too bad!!")
	}
}

```


