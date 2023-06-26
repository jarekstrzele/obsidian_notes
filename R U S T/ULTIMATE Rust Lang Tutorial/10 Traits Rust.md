#rust/traits 
[[_ LetsGetRusty Ultimate Rust Lang Tutorial]]


```rust
pub struct NewsArticle {
  pub author: String,
  pub headline: String,
  pub content: String,
}

impl Summary for NewsArticle {
  fn summarize(&self) -> String {
    format!("{}, by {}", self.headline, self.author)
  }
}


pub struct Tweet {
  pub username: String,
  pub content: String,
  pub reply: bool,
  pub retweet: bool,
}

impl Summary for Tweet {
  fn summarize(&self) -> String {
    format!("{}:{}", self.username, self.content)
  }
}

pub trait Summary {
  fn summarize(&self) -> String;
}

fn main(){
  let tweet = Tweet {
    username: String::from("johner"),
    content: String::from("Hello world"),
    reply: false,
    retweet: false
  } ;

  let article = NewsArticle {
    author: String::from("John Doe"),
    headline: String::from("the Sky is falling"),
    content: String::from("the sky is not actually falling")
  } ;

  println!("tweet summary: {}", tweet.summarize()) ;
  println!("Article summary: {}", article.summarize()) ;
 }
```


You can use default implantation
```rust
pub trait Summary {
  fn summarize(&self) -> String{
    String::from(" something be default ") 
  }
}
```


## traits as parameters
```rust
pub fn notify(item: &impl Summary){
	println!("Breaking news! {}", item.summarize())
}

// the same functionality
pub fn notify<T: Summary>(item: &T){
	println!("Breaking news! {}", item.summarize())
}

```


if you want to have the same type
```rust
pub fn notify(item1: &impl Summary, item2: &impl Summary) {
 // ...
}
```
you have to use the second syntax
```rust
pub fn notify<T: Summary>(item1: &T, item2: &T) {
//...
}
```

## multiple traits
```rust
pub fn notify(item1: &(impl Summary + Display), item2: &impl Summary ){
	// ... 
}

// the same functionality
pub fn notify<T: Summary+ Display>(item: &T, item2: &T){
	// ...
}
```


### `where` clause
this code is not readable
```rust
fn some_func<T: Display + Clone, U: Clone + Debug>(t: &T, u: &U) -> i32 {
	// .....
}
```

so you can use `where` clause
```rust
fn some_func<T, U>(t: &T, u: &U)-> i32
	where   T: Display + Clone,
			U: Clone + Debug
{
	//...
}
```


## Traits as a returned value
```rust
fn returns_summarizable() -> impl Summary {
//...
}
```



