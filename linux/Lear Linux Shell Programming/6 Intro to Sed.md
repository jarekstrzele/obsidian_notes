[[_ Intro Linux Shell]]



---
# Intro to Sed
==StreamEDitor== it edits streams

**stream**:
	- file
	- stdinput
	- stdoutput
	- takes a regular expression or a couple of regular expressions and in its simplest form transforms one thing found by a regular expression into something else

`'s/theStringToFind/theStringToReplace/'` substitude takes two regualr expressions

```shell
$ echo 'red ball'
red ball
$ echo 'red ball' | sed 's/red/blue/'
blue ball

```
`/` you can change to any other character
```shell
~$ echo 'red ball' | sed 's:ball:wagon:'
red wagon
```

---
## Suppressing output with -n, and Back expressions
`(base) jarek@jarek-Lenovo-G700:~$ sed 's/red/black/' emails.txt`

`-n  ... /p` at the end tells that all changes will be print in the  terminal
`$ sed -n 's/red/black/p' emails.txt
`


`()` anything in that parentheses is going to be a subexpression of my regular expression
`~$ sed 's/wa\(gon\)/poly\1/' emails.txt`
`\(gon\)` is the first subexpression - >`\1` refers to this first one
`\(` escaping `\`
this `sed` means: find in the file *emails.txt*  a expression 'wagon' and replace it by 'polygon'




---
## address notation
`sed 'p' lines.txt` print all lines in the file *lines.txt* twice, because we stream out every line and then print every line
but
`sed -n 'p' lines.txt` print each line once

line numbers (addresses) may preceed the command to sed:
`#` match only in this line
`#!` mach in all lines but this one
`$` mach in the last line
`#,#`  match all lines in the range
`#~#` match in the ifrst line nymber givem, then sip the second number of lines. repeat until the end of the file
`#, +#` match in this line and the folowing number of lines
`/regexp/` match in only thise lines given by this regexp (POSIX format)

`sed -n '4p'  lines.txt` print the fourth line
`sed -n '4!p'  lines.txt` print all lines but not the fourth line
`sed -n '$p'  lines.txt` print the last line 
`sed -n '2,5p' lines.txt ` print lines from 2 to 5
`sed -n '1~2p' lines.txt ` print odd lines 

POSIX
`sed -n '/[t]/p' lines.txt` print only that lines containing `'t'`

---

## Other commands
`-f` switch tells `sed` to take its regular expression input from a file 
`.sed` extention for `sed` 

`sed -nf phones.sed ~/phones.txt` -> print a report

```file.sed
# comment
#print correct phone numbers. Use with -f switch to sed
# print a title (\ followed by a newline escapes the newline):
1 i\
\
Correct Phone Numbers: \

# print only 'correct' phone numbers:
/\(\?[0-9]\{3\{ ....$/p

/\(\?[0-9]\{3\{ ....$/a

```
`i` insert text before current line
`a` append text after current line

----
## extract data
#### `awk`
`ls -l | awk '{print $1 $9}'` prints permissions and file names


