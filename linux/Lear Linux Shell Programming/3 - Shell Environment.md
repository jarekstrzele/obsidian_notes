[[_ Intro Linux Shell]]


----
# Shell Environment
**Bash** is a Linux Shell (Born Again Shell)

>[!definition: SHELL SCRIPT]
>is a collection of commands and of course those commands can be givent at the shell

```bash
$ echo 'Hello world'
Hello world
```

### `.sh`

I made a file `hello.sh`:
```sh
#!/bin/bash

echo 'Hello World'

```

change the permission to execute this file `chmod 755 hello.sh`
```bash
$ ./hello.sh 
Hello World
```

`./` in that folder, in the current directory

----
## Path
**path** is the environment ro the path names of the executable envirenments within our shell or the linux system

`echo $PATH`

```bash
$ echo $PATH
/home/jarek/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin

```

We want to run our file only by the name of this file not by `./filename.sh`

If we move our file into one of these folder (`$PATH`), we achieve our goal

```bash
$ sudo mv /usr/local/hello.sh /usr/local/bin/
$ hello.sh
FROM file

```

#### script to change folder
ccd.sh
```script
#!/bin/bash

cd /home/jarek/PROG/Billennium
```

`chmod 755 ccd.sh`

`./ccd.sh` doesn't work because it creates a new copy of shell to execute its commands in
`. ccd.sh` works well, it executes its commands in this copy

`sudo mv ccd.sh /usr/local/bin`

make alias
`alias ccd='. ccd.sh'`

---
## Intro to variable
```bash
$ echo $a
5
(base) jarek@jarek-Lenovo-G700:~$ unset a
(base) jarek@jarek-Lenovo-G700:~$ echo $a

(base) jarek@jarek-Lenovo-G700:~$ 
```

`((...))` expression
```shell
$ $ a=5
$ echo $a
5
$ echo $((a+4))
9
$ a=$((a+100))
$ echo $a
105
```

to assign : `a="this is a string"` 

```shell
$ a=5
$ b='a is $a'
$ echo $b
a is $a
$ b="a is $a"
$ echo $b
a is 5
```

---
## Saving Shell state in .bashrc

> `.bashrc` is executed every time a terminal is exacuted
> 
			
Inside this file is info that `.bash_aliases` will be executer if it exists






