[[_ Rust Programming for Beginners]]


# Drive Macro for printing info

>[!info] Drive
>It is a special macrto that is applied to `enum` and `struct`
>`#[dervie(...)]` 
>`Debug` debug printing functionaity 
>`Clone`
>`Copy`  copies the argument, so ownership is not move from `struct` or `enum`


```rust
#[derive(Debug, Clone, Copy)]
enum Position {
  Manager,
  Supervisor,
  Worker,
}

#[derive(Debug, Clone, Copy)]
struct Employee {
  position: Position,
  work_hours: i64,
}

fn print_emp(emp: Employee) {
  println!("{:?}", emp) ;
}

fn main() {
  let me = Employee {
    position: Position::Worker,
    work_hours: 40,
  };

  println!("{:?}", me) ;
  println!("{:?}", me.position) ;
  print_emp(me);
  print_emp(me);
}
```





