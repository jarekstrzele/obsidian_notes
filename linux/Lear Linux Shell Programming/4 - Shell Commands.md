[[_ Intro Linux Shell]]


---
# Shell commands
content of this note:
[[#exit status]]
[[#If statment]]
[[#test]]
[[#command line args]]
[[#Guessing Game]]
[[#LOOPS]]



---
## exit status
**exit status** 
	- is the status of the last command executed
	- `0` exit status -> success
	-`echo $?` checks the exit status

> every single command you execute  has **an exit status**
> 

```bash
$ ls Music
(base) jarek@jarek-Lenovo-G700:~$ echo $?
0

$ ls eowidj
ls: cannot access 'eowidj': No such file or directory
(base) jarek@jarek-Lenovo-G700:~$ echo $?
2
```

## If statment
`[ -e ... ]`

```shell
~$ touch foo
~$ [ -e foo ]
~$ echo $?
0
~$ [ -e czsdad ]
~$ echo $?
1
```

`if [cond]; then ...; else ... ;fi`

```shell
~$ if [ -e foo ]
> then
> echo 'foo exists'
> else
> echo 'foo not found'
> fi
foo exists

~$ if [ -e czdaq ]; then echi 'file exists'; else echo 'file not found'; fi
file not found
```

## test
test - check file types and compare values

`man test`

----
## command line args

`$#` this will tell us how many command line args there are
`-eq` equality
`$1`  the name of the script (this is the first command line argument) `$1` --> *file name*

Simple Script `fe.sh`:
```sh
 #!/bin/bash
   
 if [ $# -eq 1 ];then
   if [ -e $1 ]; then
     echo "file $1 exists"
   else
     echo "file  $1 not found"
   fi
 else
   echo "usage: fe filename - report the existance of a file"
 fi
       
```

->
```shell
$ vim fe.sh
$ chmod 755 fe.sh
$ ./fe.sh test.txt
file test.txt exists
$ ./fe.sh foo.txt
filefoo.txt not found
```

----
## Guessing Game
```shell
!/bin/bash
  2 
  3 # if there is one arg:
  4 if [ $# -eq 1 ]; then
  5   # generate a random number between 1 and the argument:
  6   # seed with the PID of the script:
  7   RANDOM=$$
  8 
  9   # debug only:
 10   # ps
 11   # end debug
 12 
 13   # get a random number between 0 and $1 - 1 inclusinve:
 14   correct=$(( RANDOM % $1 ))
 15   # add one:
 16   correct=$(( correct + 1 ))
 17 
 18   # set up an initially incorrect guess:
 19   guess=0
 20 
 21   # debug only:
 22   # echo "number is $correct"
 23   # end debug
 24 
 25   # a variable to count the guesses:
 26   count=0
 27 
 28   # get guesses from user until they
 29   # get it right:
 30 
 31   while [ $guess -ne $correct ]
 32   do
 33 
 34     #get a guess
35     echo "Guess my number (1 - $1) ->"
 36     read guess
 37 
 38     # count this guess:
 39     count=$(( count + 1 ))
 40 
 41     # too high, too low, or just right?
 42     if [ $guess -gt $correct ]; then
 43       echo "TOo high! Try again -> "
 44     elif [ $guess -lt $correct ]; then
 45       echo "Too low! Try again ->"
 46     else
 47       echo "Correct. Guessed $correct in $count tries!"
 48     fi
 49 
 50   done # end of while loop
 51 else
 52   echo "USAGE: guess <num>, where the correct answer will be\n"
 53   echo "a random number in the range 1..num inclusive.\n\n"
 54 
 55 fi
                 
```


----
## Loops
### sequence `seq`
```shell
$ seq 1 5
1
2
3
4
5

```


```shell

  1 #!/bin/bash
  2 
  3 # counts from 1 to $1 using for, while, and untile loops
  4 # ensure only one argument:
  5 
  6 if [ $# -eq 1 ]; then

  7   # a counter variable:
  8   counter="1"
  9 
 10   echo "for loop:"
 11   # sekwencja jest tworzona tylko raz
 12   # specific rang ->
 13   # for i in {1..7}
 14   for i in $( seq 1 $1); do
 15     echo $i
 16   done
 17   
 18   echo "while loop:"
 19   while [ $counter -le $1 ]; do
 20     echo $counter
 21     counter=$(( counter + 1 ))
 22   done
 23 
 24   counter="1"
 25   
 26   echo "until loop:"
 27   until [ $counter -gt $1 ]; do
 28     echo $counter
 29     counter=$(( counter + 1 ))
 30   done
 31 
 32 else
 33   echo "usage: $0 <count> - where count is the value to be"
 34   echo "counted to."
 35 fi
 36 
 37 

```


----
## The case Statement
menu
```shell
  1 #!/bin/bash
  2 
  3 echo "Please choose an option: "
  4 echo "1 change to directory one"
  5 echo "2 change to dir two"
  6 echo "3 change to dir three"
  7 echo "Q quit"
  8 read choice
  9 
 10 bashdir='~/PROG/Billennium/linux/'
 11 
 12 case $choice in
 13 1)
 14   cd ${bashdir}one/
 15   ;;
 16 2)
 17   cd ${bashdir}two/
 18   ;;
 19 3)
 20   cd ${bashdir}three/
 21   ;;
 22 [Qq])
 23   ;;
 24 *)
 25   echo 'Incorrect menu entry.'
 26 esac
 27 
```

`. meny.sh`




