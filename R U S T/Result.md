#rust/result 

>[!info] `Result`
> It is a generic enumeration type that represents the result of an **operation that may fail**

```rust
enum Result<T, E> {
    Ok(T),
    Err(E),
}

```

- `T` is the type of the value that represents success
- `E` is the type of the error that represents failure
- `Ok(T)` indicates that the operation was successful and contains the result value of type `T`
- `Err(E)` indicates that the operation failed and contains the error value of type `E`






