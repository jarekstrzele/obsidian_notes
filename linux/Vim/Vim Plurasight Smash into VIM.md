#vim #plurasight #stewart_andrew


# Smash into VIM


## Philosophy
### Modal Editing
- navigation is more important than writing
`h j k l`
- modes: normal, insert, visual, replace, command-line
- `3j` move down 3 lines, `f{` find next bracket, `i` prepare to insert text, ....
- `iWar and Peach<esc>` insert text, then stop
- use `<esc>` a lot (to be normal mode)
- `d$` delete through end of line


### Operators
`d2w` delete two words
`d` operator
`2` count
`w` motion

### help
`:h <name_of_comment>` vim help system is extremely  useful
to quit `:bd` buffer delete


### conventiotns
- uppercase commands are usually  supersized versions of their lower case counterparts
`i` insert text at cursor (activates **Insert** mode)
`I` insert text at start of line

`w` move forward by one word
`W` treats contiguous code as one word and jumps forward to the next to meaningful code word
`b` move backward by one word

tojest ciągłytekst, i ciekawe jakdziałają;duze ; listery

----
# Basics
`hjkl` left, down, up, right
`yy` yank line (copy)
`p` paste below cursor
`P` paste above cursor

`i` insert text before cursor
`a` append text after cursor

`6l` forward 6 letters

`fN` jump forward to first 'N'
`3fN` jump forward to third 

#### `u` undu
#### `ctr+r` redo

`w` forward one word
`cw` change word

`vim -N fileName`
> `-N` No-compatible mode.  Resets the 'compatible' option.  This will make Vim  behave  a bit better, but less Vi compatible, even though a .vimrc file does not exist.

`:syntax enable`
`:set syntax=apache`
`:set hidden` to handle mutiple files better

---
# Editing files










