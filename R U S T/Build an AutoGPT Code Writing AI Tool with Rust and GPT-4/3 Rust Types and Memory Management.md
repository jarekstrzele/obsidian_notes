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


## String Literals and Static (Read-Only) Memory


























