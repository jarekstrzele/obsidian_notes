#rust 

>[!info] idiomatic
>1. expressions that are natural to a native speaker
>2. appropriate to the style of a particular group

So we are talking about using Rust  like someone  who has used it every day for years

TWO TOOLS:
1. `rustfmt` (`rust` -> `fmt` (format)) it formats the code for you
	1. `cargo fmt` it is the command we will run to automatically  reformat our code
	2. it does take care of most of your whitespace and punctuation issues so that your code layout is idiomatic
	3. it doesn't compile the code 
2. `clippy` 
	1. `cargo clippy` - it compiles the code and checks for over 450 specific types of problem from one of four category:
		1. STYLE
		2.  CORRECTNESS
		3.  COMPLEXITY
			1. if you want to left your complexity,   you can add something like that:  `#[allow(clippy::too_many_arguments)]` (so clippy accept too many args in your function)
		4.  PERFORMANCE







