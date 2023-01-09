[[_ Intoduction]]

---
# Inserting, Changing, Replacing, and Joining

`shift + i` the cursor jumps to the first non blank character in the line and you are placed into **insert mode**
`0` the same but you stay in normal mode
`a` moves one place after the cursor and changes a mode **into insert**

`shift + a` the end of line + the insert mode

`o` the cursor goes to the next line and you are in the insert mode
`shift + o` the cursor => new line and insert mode

###### create a line that contains 80 asterisks
normal mode
	- type `80`
type `i` to change mode into insert mod
	- type `*`
type `esc`

###### create 5 line that begin with "#"
normal mode
	- type `5o` => insert mode
	- type `#` 
	- type `esc`

###### create 4 line that begin with "10.11.12"
normal mode
	- type `4o`
	- type `10.11.12`
	- type `esc`