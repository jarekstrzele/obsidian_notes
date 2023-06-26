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

```

