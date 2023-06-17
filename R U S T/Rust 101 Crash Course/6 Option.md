#rust/option 

>[!info] `Option`
>- a type that may be one of two things
>	- SOME data of a specified type
>	- NOTHING
>- Use in scenarios where data may not be required or is unavailable
>	- unable to find something
>	- ran out of items in a list
>	- form field not filled out

definition:
```rust
enum Option<T>{
	Some(T),
	None
}
```







