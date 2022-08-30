[[_ Preface Git - Practical Guide]]

---
Mac Terminal Commands overview => [**https://support.apple.com/guide/terminal/keyboard-shortcuts-trmlshtcts/2.10/mac/10.15**](https://support.apple.com/guide/terminal/keyboard-shortcuts-trmlshtcts/2.10/mac/10.15)

Windows Command Prompt overview => [**https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/windows-commands**](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/windows-commands)

The "new" Windows Powershell (not used in the course) => [**https://docs.microsoft.com/en-us/powershell/scr**](https://docs.microsoft.com/en-us/powershell/scripting/overview?view=powershell-7)


---
			`man command_name` manual of this command
		
# Mac ter & Windows Command Prompt




## In Mac:
**terminal** text input environment ("hardware")
**Shell** text input interface ("software")
- older :  Bash
- zsh (Z-Shell)

## In Windows:
- older : Command Prompt (cmd)
- PowerShell
- Git Bash (bash emulation for Windows)

---

## Absolute vs Relative Path
`pwd` shows a __absolute__ path (i.e. _/home/jarek/PROG/Billennium/docker/docker_python/d4py/section-3/basic-env_)
If a folder name includes a space, use `\ `.

__relative__ path
means starting from my surrent location
`cd ..`

---
`mkdir folder_name` make directory
`mkdir z\ space` -> 'z space'

`touch filename.txt`  creates a new file
`$touch style.css script.js`

`rm one_file.txt` removes a file from the disc
`rmdir folderName` removes ==an empty folder==
>   -r, -R, --recursive
              remove directories and their contents recursively

`rm -R folder_name` removes a folder


---
## FLAGS
allow you to add additional options to your commands

`ls -s` -> 
```
total 0
0 index.html  0 style.css

```

















