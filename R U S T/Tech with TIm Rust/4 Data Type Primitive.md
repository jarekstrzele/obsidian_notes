[[_ Rust Tech with Tim]]

>[!info] Primitive Data Type
>Primitive data types are the basic or fundamental data types used to delare a variable 


# Scalar data type
>[!info] SCALAR DATA TYPE
>A scalar data type is something that has a finite set of possible values, following some scale, i.e. each value can be compared to any other value as either equal, greater or less
> - integer
> - floating-pont
> - boolean
> - character


## Integer
`let x = 2 ;` implicite this is integer type
`let x: i32 = 2 ;` explicite integer type

negative and positive number: `i8, i16, i32, i64, i128` 
only - positive: `u8, u16, u32, u64, u128`

## Floating

### `f32` 

### `f64` default

## Boolean
`: bool`
`0, 1`
`false, true`

## Character 
`let letter: char ='a' ;` (single quatation mark)





# Compound data type
>[!info] COMPOUND DATA TYPE
>in Computer science, a composite data type or compund data type is any data type which can be constructed in a program using th programming language's primitive data types and other composite types
> - tuple
> - array

## TUPLE
fix-length sequence of elems , immutable
```rust
let tup: (i32, bool, char) = (1, true, 's') ;

// access
println!("{} ", tup.0 ) //->1    tup.1->true


// mutable tuple
// you can change a type of tuple
let mut tup: (i32, bool, char) = (1, true, 's') ;
tup.0 = 10 ;
// or change 
tup = (1110, false, 'k') ;
```

## Array
the same type of elements, fixed length
```rust
fn main(){
	// by default is immutable
	// :[type, length]
	let arr: [i32; 5] = [1,2,3,4,5] ; //only int, only five elems
	let mut arr = [1,2,3,4,5] ; //only int, only five elems
	arr[4] = 44 ;
	println!("{}", arr[4])
}
```




