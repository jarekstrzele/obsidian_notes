[[_ Ultimate Rust Crash Course]]

# Scalar types
- integer
- float
- boolean
- character


#### integer
unsigned: u8, u16, u32, u64, u128
sifned: i8, i16, i32, i64, i128

decimal: `1_000_000`
hex: `0xdead_beef`
octal: `0o7754_3211`
binary: `0b1111_0011`
Byte (u8 only): `b'A'`

#### float
```rust
let x: u16 = 5;
let y: f32 = 3.14;

//also:
let x = 5_u16;
let y = 3.14_f32 ;
```

#### `Bool`
`true`
`false`

#### `Char`
let my_letter = 'a' ;
`string` doesn't use `char`

-------------
# Compound types
They gather multiple values of other types into one type

## `tuple`
It store multiple  values of ANY TYPE.
```rust
let info: (u8, f64, i32) = (1, 3.3, 999) ;
```

access by DOT SYNTAX
```rust
let jets = info.0 ;
let fuel = info.1 ;
let ammo = info.2 ;
```

access all at once:
```rust
let (jets, fuel, ammo ) = info ;
```

**arity** means how many items are in the tuple. maybe 12 items are maximum

## `array`
```rust
let buf_1 = [1,2,3] ;

let buf_2 = [0; 3] ; //[value, how many] [0, 0, 0]
```


-------------
# control flow

## `if`
`if condition {} else {}`

`if` it is an expression (returns a value), not statement (doesn't return a value) - so:
```rust
let msg = if num == 5 {
		"five" 
	} else if num == 4{
		"four" 
	} else {
		"other"
	} ;

```

generally:
```rust
num = if a  { b } else { c } ;
```


## `loop{}`

```rust
'bob: loop {
	loop {
		loop {
			break 'bob; // breaks named loop
		}
	}
}
```


## `while condition {}`

## `for`
```rust
for num in [7,6,5,4].iter() {
 ///
}

let array = [(1,2), (3,4)] ;

for (x,y) in array.iter(){
 ///
}

//R A N G E
for num in 0..50 {
  //// 0 - 49
  /// 0..=50  -> 0 -50
}
```


----
# String
#rust/string 

There are at least 6 types of strings int the Rust standard library!!!!!

Two of them are very often used:
1. `&str` string slice 
	1. a literal string is always  a borrowed string slice `let msg = "hello";`
	2. data in that type of string CANNOT BE MODIFIED
	3. ==it is made up  of a pointer to ==:
		1. some BYTES
		2. and a LENGTH
2. `String`  
	1. its data can be modified
	2. `to_string()` creates a `String` (e.g. `let msg = "abc".to_string() ;`)
	3. `String::from()` create a String (e.g. `let msg = String::from("abc") ;`)
	4. ==it is made up of a pointer to==:
		1. some BYTES
		2. and a LENGTH
		3. and a CAPACITY (may be higher than what is currently being used )

you cannot have access by `[index]` with `String`
iterator have `.nth(3)` and use it instead of `[index]`







