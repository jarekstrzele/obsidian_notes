
# 18 shell commands

## Poruszanie się po ścieżkach
powrót do poprzedniej lokalizacji `cd -`
```shel
(base) jarek@jarek-Lenovo-G700:~$ cd /etc
(base) jarek@jarek-Lenovo-G700:/etc$ cd -
/home/jarek

```

powrót do folderu domowego: `cd ~`

clear the screen: `ctr+l` (save history)
reset the shell: `reset`

##### `pushd   popd`
`pushd` command to manipulate the direcory stack
`d` in `pushd` means directory, it means "push the direcotry path onto the stack" (stack LIFO)
```shell
(base) jarek@jarek-Lenovo-G700:~$ pushd ~/Desktop
~/Desktop ~
(base) jarek@jarek-Lenovo-G700:~/Desktop$ dirs -l -v
 0  /home/jarek/Desktop
 1  /home/jarek
(base) jarek@jarek-Lenovo-G700:~/Desktop$ pushd ~/PROG
~/PROG ~/Desktop ~
(base) jarek@jarek-Lenovo-G700:~/PROG$ dirs -l -v
 0  /home/jarek/PROG
 1  /home/jarek/Desktop
 2  /home/jarek

```

`pushd directory_name` -> the current dir will be directory_name and this directory will be added to the stack


### front back ground
1. You opened a file (`vim tt.txt`),
2. You want (without closing the file) to write something down in the terminal, sa
3. `ctr+z`
4. to return to the file `fg` (front ground)


### sudo
1. you wrote `apt update` -> error
2. Write `sudo !!` and linux will execute `sudo apt update`


### history `history` an run `!23`
`history` shows all command executed in the shell
```shell
$ history
    1  git stash apply ls
    2  git stash apply list
    3  git stash list
    4  git stash apply 2
    5  vim file1.txt 
...
```

if you want to run e.i. `vim file1.txt`, write down `!5`









