[[_ 0 Learining Haskell Programming]]

# Create
## `stack new words`

 may you have to add some config info
 to ` vim ~/.stack/config.yaml`
 ```
 templates:
	 params:
		 author-email: ...
		 author-name:...
		 category:..
		 caopyright: ..
		 github-username:..
```

# Compile
## `stack ghci` 
inside the folder project


# declare a library module

```haskell
module Lib
    ( someFunc
    ) where

someFunc :: IO ()
someFunc = putStrLn "someFunc"


```

`(someFunc) where`a list of exported functions and symbols  
`Lib` a module name

`stack build` build the project , if there are some changes









