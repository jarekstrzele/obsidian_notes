
>[!inf] RULES
>- a package must have at least one crate
>- a package could have either zero library crates or one library crate  
>- a package could have any number of binary crates `src/bin`



# Package
`cargo new projectName` --> generates a package
in `Cargo.toml` you will find 
```toml
[package]
name = ""
version =
authors = 
edition


```


### `cargo new --lib projectName`
- structure is the same
- instead of `main.rs` you have `lib.rs`> `test module`



# Crates
a new package stores **crates**
Crates can be:
- ==binary crates==, so you can execute it
- ==library crates== which is code that can be used by other programs

Crates contain modules.

**a crate root** (e.g. `main.rs`) is the source file that the rust compiler starts at when building your crate

**library** (`src/lib.rs`)
if `lib.rs` defied in the root of your source directory then rust will automatically create a library crate with the same name as your package and `lib.rs` will be the create root 

Your `.toml` file may have no annotation, but you have two crates `main.rs`, `lib.rs`



# Modules
They allow you to organize a chunk of code and control the privacy rules


# Workspace
They contain packages









