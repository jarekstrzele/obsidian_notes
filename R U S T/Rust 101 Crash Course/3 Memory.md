#rust/memory 

>[!info] memory
> - memory is stored using binary `0`, `1`
> - computer optimized for bytes *1 byte == 8 contiguous bits*
> - fully contiguous

>[!info] addresses
>- all data in memory has an "address"
>	- used to locate data
>	- always the same - only data changes
>- usually don't utilize addresses directly
>	- variables handle most of the work

>[!info] offsets
>- items can be located at an address using an "offset",
>- offsets begin at `0`
>- represent the number of bytes away from the original address (normally deal with indexes instead)

![[rust_address_offset.excalidraw | 600]]









