[[_ 0 Happy Learn Haskell]]

```haskell
main :: IO()
main = putStrLn (message "Dave")

message :: String -> String
message name
	| name == "Dave" = "I can't do that."
	| name == "Sam" = "Play it again."
	| otherwise = "Hello."

msg2 :: String -> String
msg2 name =
case name of
	"Dave" -> "I Can't do that"
	"Sam" -> "Play it again"
	_ -> "Hello"

msg :: String -> String
msg name =
	if name /= "Dave"
	then if name == "Sam"
		then "Play it "
		else "Hello"
	else "I can't do that"
```
















