[[_ Vim intro]]


---
## Vim key bindings and Vim Key Functions

in google: vim cheetsheet
![[images/vim-commands-cheat-sheet-by-pnap.pdf]]

![[images/vim_cheet_sheet1.png|700]]

[[images/vim_cheet_sheet1.png]]


The change from insert mode to normal mode:
##### Undo  `u` in normal mode
`3u`
`5u`
##### Redo  `ctr+r` in normal mode
`2r`
`6r`

##### visual mode is for selecting
#vim/visual 
`v`


### delete (cut)
`d` delete  `4d  2d   6d` <=> `c` like `d` + insert mode
`dd` delete a hole line `5dd`  <=> `cc` like `dd` + insert mode
`D` from cursor to the end of line
`C` like `D` + insert mode


### yank (copy)
`y` yanking / cutting `2y  3y  8y`
`yy` yank a hole line == `Y` (are the same)
`p` paste  `2p   10p   32p`
`p` paste below a line or before a cursor
`P` paste above a line  or after

### replace
`r` replace
``

### jumping
`w` jump to the next word
`W` jump to the next word (words are separate by "space")
`b` jump to the back word
`B` jump to the back word (words are separate by "space")
`e` jump to the end of the word
`I` jump to the beginnign to the line
`0` jump to the beginning ot the line
`$` jump to the end of the line

`gg`
`G`
`123G` === `:123`

### mixing
`dw` delete one word (next)
`d2w` delete two words (next)
`d3b` delete three words (back)
`d0` delete every thing from the cursor place to the begining of the line


cursor is in the word, so to delete a hole word `diw` *delete inside word*
`ciw` change inside the word
`yiw` yank inner word
`diw` delete inner word
`ci"` change all letter in the quotation mark
`d7w` delete seven words

The cursor is on the opening bracket, so `%` move to the closing bracket and vise versa 
`d%` delete brackets and its content

??????????
`t(` move to before the `(`
`f(` move to the first occurence of the `(`
`dt(` delete everything until you find `()`
`df(` delete everything between the cursor and the `(` with `(`
`T` and `F` do the same but backlwards

----
### visual line mode
`shift + v`

### visual column/block mode
`ctr+v`

---
### indendation
`==` to indent
or
use visual line mode and `=`
or
`gg=G`  indent all file


