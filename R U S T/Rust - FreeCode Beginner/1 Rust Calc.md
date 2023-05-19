#rust #rust/format #rust/match #rust/return

[[_ 0 Rust]]

## Calc first version
```rust
use std::{env::{args, Args}, result};

fn main() {
    let mut args:Args = args();
  
    let first: String = args.nth(1).unwrap() ;
    let operator: char = args.nth(0).unwrap().chars().next().unwrap() ;
    let second: String = args.nth(0).unwrap() ;
  
    let first_num: f32 = first.parse().unwrap() ;
    let second_num = second.parse::<f32>().unwrap() ;
  
    let result: f32 = operate(operator, first_num, second_num) ;
    println!("{:?} ", ouput(first_num, operator, second_num, result));

}
  

fn operate(operator: char, first_number: f32, second_number: f32) -> f32 {
    if operator == '+'
    {
        // you can user `return` but you have not
        return first_number + second_number ;
    } else if operator == '-' {
        return first_number - second_number ;
    } else if operator == '*' {
        return first_number * second_number ;
    } else if operator == '/' {
        return first_number / second_number ;
    }
    else {
        return 0.0;
    }
}

fn ouput(first_number: f32, operator: char, second_number: f32, result: f32) -> String{
    format!("{} {} {} = {}", first_number, operator, second_number, result)

}
```

```bash
> cargo run -- 11 * 2 
"11 * 2 = 22"
```

## Calc second version

change `operate` function
```rust
fn operate(operator: char, first_number: f32, second_number: f32) -> f32 {

    match operator {
        '+' => first_number + second_number,
        '-' => first_number - second_number,
        '/' => first_number / second_number,
        '*' | 'x' | 'X' => first_number * second_number,
        _ => panic!("Invalid operator used.")

    }

}
```

```bash
> cargo run -- 111 X  211
"111 X 211 = 23421" 
```

now

## to build calc
### `cargo build --release` (build and add some optimalizations)


```bash
> ./target/release/calculator 10 - 4.33
"10 - 4.33 = 5.67" 
```




