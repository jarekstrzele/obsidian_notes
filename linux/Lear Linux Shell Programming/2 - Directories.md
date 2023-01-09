[[_ Intro Linux Shell]]

---

# Directories

`mkdir directoryname`
`cd ~`
`rmdir directoryname` (It must be empty)

==remove a non-empty directory==
`rm -r directory_name` delete recursevly non-empty folder
`rm -tv dir_name` delete and show what has just hapened

---
## Wildcards
#wildcards 

`rm filename` delete a file
`rm *` remove any files 

- `*`  wildcard (zero or more character)
- `?` exactely one character
`ls tes*`
`ls ?e`
`ls *file`
`le te?t*` -> test tests, testsssdfw, 
					 teqt teqtsd ...


## File operations
`cp file1 file3` copy from to
`mv what to` moves files from what to to
to rename
`mv files1 new_name_of_file1`


----
## Redirection and Piping

`cat filename` (concatenate a file to the file system, show its content to the standard out put (a console screen)

`cat > file1 ` a symbol `>` ==redirects== whatever the input is to the output
(what yoy write on the screen will be written into the file)

`wc` word count, print newline, word, and byte counts for each file
`man wc` help about `wc`
`wc -w` print the word counts

```bash
~$ cat > new_file
this is a file
$ cat new_file 
this is a file

$ wc -w new_file 
4 new_file

// take input from new_file
$ wc -w < new_file 
4

$ wc -w < new_file > wordcount
$ cat wordcount 
4
```

`>` and `<` allows us to redirect from what would be standard input, standard output, to a file or from a file

`>` redirect output to a file
`<` redirtect input from a file

---
==PIPING== another way to redirect input/output
#pipe

`|` 

```bash
$ ls -l | wc -l
28
```
take the output of `ls -l` and piped it to the input of word count

`|` (the pipe characheter): send the output of one program to the input of another






