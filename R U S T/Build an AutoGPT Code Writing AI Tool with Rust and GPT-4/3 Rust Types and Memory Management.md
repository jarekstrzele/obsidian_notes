[[_ Rust Build with GPT-4]]

#rust/type 

int, float, char, bool, fixed-size arrays, tuples -> on stack
`Vec<T>` resizable arrays on Heap
`String` on Heap
&T, &mut T references on Stack
&str immutable string references on (depends)
`Enum`, `Struct` on (depends)

# Stack vs Heap - memory management

## stack
>[!definition] STACK
> It stores stack frames

 You start a program and it will get a fixed size memory for stack (e.g. to allocate memory for variables)

![[stack_rust.excalidraw]]


## Heap
![[heap_rust_stack.excalidraw | 700]]





`let x: u8 =40 ;` on the stack

`let arr: Vec<u8> = vec![1,2,3,4,5] ;` on the heap
`arr.push(10)`

`arr_2` is the reference of `arr`
`let arr_3 = &arr[0..3] ;` (1,2,3) , the reference on the Stack pointing to a value on the Heap


`let mut s:String = String::from("Shai hountng") ;`  on the heap
`s.push(' ') ;`

`let s_2 = &s[1..3] ;` the reference on the stack pointing to a value on the Heap

`const MY_INT = 10 ;`  == `static MY_INT = 10 ;` it can't be mutable `const mut` generates an error

-----------
## String Literals and Static (Read-Only) Memory

























