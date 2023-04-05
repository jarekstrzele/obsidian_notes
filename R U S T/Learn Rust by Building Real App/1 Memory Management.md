#rust/memory 

[[_ Learn Rust by Building Apps]]

-------

# Stack
#rust/stack  

>[!info] Stack
>It is a special region of the process memory that stores variables created by each function
> > The memory for each functio is called ==a stock frame==:
> > 	- this is where our local variables ive for every function
>  
>  > For every function call a new stack frame is allocated on top of the current one
> the size of every variable on the stock has to be known at compule time!!
> > > if we want to store an array on the stack, we have to specify exactly how many elements it will hold
> > 
> 
> When a function exits it's stack frame is released



--------
# Heap
- it is a region of tjhe process memory that is NOT automatically managed
- it has no size restrictions
- it is accessible by any function, anywhere in the program
- heaap allocations are expensive and we should avoid them when possible

a memory flow
- allocate the memory on the heap for the value
- write the value on the heap
- on the stack you write a memory address to the value that was written on the heap
- if your stack is empty, the value is still on the heap (MEMORY LEAK)
remember: you have to deallocate the memory


--------
# Smart Pointers
It is a wrapper around the roll pointer adding additional capabilites to it
- allocate the memory on the heap for the value
- write the value on the heap
- on the stack you write a memory address (==wrapped into smart pointer==) to the value that was written on the heap
- if you delete the smart pointer (on the stack), it deletes your value from the heap

.g. `let e = Box::new(7)` the address of the value `7`  is wrapped into a smart pointer











