#rust/derive 

## `#[derive(Debug)]`
If you add it to `enum` or  `struct`, you would be able to print the `enum` or the `struct` without `match` syntax.
```rust
#[derive(Debug)]
enum Position {
	Manager,
	Supervisor,
	Worker,
}

#[derive(Debug)]
struct Employee{
	position: Position,
	work_hours: i64,
}

fn main(){
	let me = Employee {
		position: Position::Manager,
		work_hours: 40,
	} ;

println!("{:?}", me.position) ;
println!("{:?}", me) ;
}
```

## `#[derive(Clone, Copy)]`
it allows to automatically make a copy when you're storing it into a struct or function

```rust
#[derive(Debug, Clone,Copy)]
enum Position {
	Manager,
	Supervisor,
	Worker,
}

#[derive(Debug,Clone, Copy)]
struct Employee{
	position: Position,
	work_hours: i64,
}

fn print_employee(emp: Employee){
	println!("{:?}" , emp) ;
}

fn main(){
	let me = Employee {
		position: Position::Manager,
		work_hours: 40,
	} ;

	print_employee(me) ; // it makes a copy of me
	print_employee(me) ; // it makes a copy of me
}
```








