[[_ Intro Linux Shell]]



----
# Regex with Grep and Sed

==Everything in UNIX is a file==

## grep
> ![[global regular expression print]]
> searches for patterns within files and then prints out the lines by default where those patters occur

`ls -l /usr/bin > bindir.txt` list content of bin and write it into the file bindir

`' pattern '`
`grep '-' bindir.txt`
`grep '^-' bindir.txt` the first character is `-`
`grep 'e$' bindir.txt` finds all files that end with 'e'

-----
## switches
#### `-i   -v   -c` 
`grep 'Aug' *dir.txt` searches 'Aug' in all files (names is ending with 'dir.txt')

`-i` ignore case
`grep -i 'Kwi' *dir.txt` the `-i` switch ignores the case

`-v` invert the match
`grep -v 'kwi *dir.txt'` all the don't have 'kwi'

`-c` count found lines
`grep -c 'kwi' *dir.txt` ->
```shell
$ grep -c 'kwi' *dir.txt
bindir.txt:166
etcdir.txt:92

```

#### others `-l  -L  -n  -h`
`-l` print file names having matches
`grep -l '^d' *dir.txt` show that files in which rows start with 'd'
```shell
$ grep -l '^d' *dir.txt
etcdir.txt # only in this file are some rows that start with 'd'

```

`-L` print file name not having matches
```shell
$ grep -L '^d' *dir.txt
bindir.txt

```


`-n`  print line numbers of matching lines
tell us the line number of the line in which the regular expression matching pattern was found

`-h` do the same as `-n` but don't print file names

### man grep
`-E,  --extended-regepx`
```
-F, --fixed-strings
              Interpret PATTERNS as fixed strings, not regular expressions.
```

---------
## PIPING
```shell
$ ls -l /usr/bin | grep '^-'

$ ls -l /usr/bin | grep 'grep$'

$ echo 'ABC' | grep 'A'
ABC

```

`grep` can be piped `|` the output of any prog that writes to stdout
`^` anchor the regexp to the begining of the line
`$` anchor to the end of the line


---
## Meta characters in Regular Expressions
examples of meta characters:
`^  $  .  [ ]  { }  -  ?  *  +  ( )  |  \`
`^` the beginning of line
`$` the end of line
`\` matches what follows it (allows meta characters to be matched)
`.` any character
**parentheses** are used for grouping or in 'back expression'
	`[ ]` a set of characters, match only one within the set
	`^` at the beginning of bracketed expression negates the expression
	`[ABC]` means 'look for any single char that ==is in== the set A, b, c'
	`[^ABC]` means 'look for any single char that ==is not in== the set A, B, C'

### quantifiers
in extended regexps( `grep -E...`):
- `?` matches the preceding expression 0 o 1 times
- `*` matches 0 o more times
	`.*` zero or more any character
- `+` matches 1 or more time

an exact number of matches can be specified by  `{n,m}` where `n` is the least number to match and `m` is the most
- `{n}` match exactly `n` times
- `{n,m}` match at least `n` and most `m` times
- `{n, }` match `n` or more times
- `{,m}` match at most `m` times

## Alternation
- `|` matches either what is on its left or what is on its right
	- `ABC | XYZ` matches either `ABC` or `XYZ`, but not `AXY` 
	- `[ABC|XYZ]` matches any single character in the brackets appearing once (<=> `[A-CX-Z]`)
- alternation is a feature of extended regular expressions (`grep -E...`)


## Back references
- the (and) meta characters are used for grouping regexps into *sub-expressions* 
	- this might be done to make the expression easier to read or for disambiguation but
	- it's also done to refer back to part of a regexp if there is a replacement clause
		

---
# Example of validating e-mail addresses
`$ grep -E '^[A-Za-z].*@[A-Za-z].*\.(com|com|edu|net|tv)' emails.txt > correct.txt`
`
reverse
`$ grep -Ev '^[A-Za-z].*@[A-Za-z].*\.(com|com|edu|net|tv)' emails.txt > incorrect.txt`


----
# Example of validating US Phone Numbers
`grep -E` extended regular expression
optional: `'\(?` there will be zero or one opening parentheses

three digit: `[0-9][0-9][0-9]`  or `[0-9]{3}`

`'\)?' may be zero or one closing parentheses`













