[[_ 0 Start Master Bash Shell]]


----
# Bash Scripts
## Shell
>[!Shell]
> - A ==program== that **interprets** the commands you type in your terminal and **passes** them on th the ==operationg system== 
> - the *purpose* of the shell is to make it more convenient for you to issue commands to your computer
> - it is command-line interpreter



![[shell.excalidraw|400]]

## Bash
>[!BASH]
> - is the most popular shell
> - BASH = Bourne Again SHell
> - Based on the Bourne SHell (sh) created by Stephen Bourne in 1979
> - it is ==fast==, has a lot of ==features== is very ==commonl used==



## Script
>[!Script]
>- a shell script is a fiel containing commands for the shell
>- shell reads the script and executes the commands one by one, as if you entered them into the command
>- ==a bash script== is simply a file containing commands for the Bash shell
>- scripts allow you:
>	- ==automate== tasks
>	- ==save== time
>	- ==increase== reliability
>- 




----
# Bash Script Structure
## Core components
**shebang line**
```bash script
#!/bin/bash
```

```shell
$ file first_script 
first_script: Bourne-Again shell script, ASCII text executable
```

`#!/usr/bin/python3` -> ...:Python script ...

```bash script
#!/bin/bash

echo "First script"
exit 0
```
`exit value` value from 0 (success) to 255

execute permission: `chmod +x name_of_script`
run the script: `./name_of_script`

## Professional Components
Comments:
`# comments`

```bash
  1 #!/bin/bash
  2 
  3 # Author: Jarek Strzelecki
  4 # Date Created: 31/12/2020
  5 # Last Modified: 02/07/2022
  6 
  7 # Description
  8 # print "this is my first script" to the terminal
  9 
 10 # Usage
 11 # firstscrip
 12 
 13 echo "this is my first script"
 14 exit 0
 15 
 16 
~    
```




