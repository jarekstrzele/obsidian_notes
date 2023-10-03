#rust #udemy #gavadinov_lyubomir
[[2 Memory Management]]
[[3 Building a Command Line Application]]


---------------
# RUST IS A MODERN SYSTEMS PROGRAMMING LANGUAGE:
- memory safe
- no NULL
- no Exceptions
- modern package manager (`cargo`)
- no data races

`rustc --version` rust compiler
`cargo --version`  
`rustup --version` tool chain installer (to update compiler or cargo)

-------------
# Tools

**tools**
https://www.rust-lang.org/tools

vs code extension:
- THe Rust Programmin Language
- crates

--------------
# `cargo`

**cargo**
### `cargo new project_name`

*packages*/**crates** : https://crates.io
for example: crate `rand`:
- `cargo add rand`  or
- add `rand = "0.8.5"` to `Cargo.toml` file as
```toml

[dependencies]
rand = "0.8.5"
```

or 
`cargo install cargo-expend`
Rust is release in three different channels with different levels of stabillity:
1. *stable*
2.  *bitter* (candidate for the next stable version)
3.  *nightly*

`rustup toolchain list` -> list of toolchain
`rustop toolchain install nightly-x84_64-unkonown-linux-gnu`

------------
# Build and Run 
to **build** project
`cargo build`

to **run** project
`cargo run` (build and run)
