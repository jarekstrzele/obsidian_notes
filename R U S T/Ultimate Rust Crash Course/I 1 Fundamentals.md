[[_ Ultimate Rust Crash Course]]

**Rust** is a systems programming language:
- safety
- concurrency
- speed
- from 2006 Graydon Hoare (Mozilla from 2009), version 1.0 in 2015

this course: github: ultimate_rust_crash_course

---
# Crago
**cargo** 
- package manager
- build system
- test runner
- documentation generator

#### `cargo new hello_world`
- semantic version (e.g. 0.1.0)

#### `cargo run`
`target/debug/hello`  (executable file of your project, so you can run it directly)
##### `cargo run --release` to compile without debug symbols
(the file will be in `target/release` sub-folder)


------
# variable
- statements are terminated by semicolons
- mimic syntax from other languages
```rust
let bunnies: i32 = 4 ;
let (bunnies, carrots) = (8,  50) ;

```
- variable are immutable by default





