[[- Diving Deeper into Git]]

----


# The stash 'git stash'
#git/stash

start wtih
	one file + one commit + master branch

>[!note] dictionary
>*stash*  schowek, skrytka magazyn

the **stash** is kind of an internal memory where you can save uncommitted unstaged changes:
- you can save these changes
- and come back to the latest commit (code without these changes)
- later you will be able to add these changes to your code

`git stash`

```bash
$ git stash                                                                                  
Saved working directory and index state WIP on master: cbb881b first commit                     
```

to return these changes:
```bash
$ git stash apply                                                                            
On branch master                                                                                                                                                                            
Changes not staged for commit:                                                                                                                                                              
  (use "git add <file>..." to update what will be committed)                                                                                                                                
  (use "git restore <file>..." to discard changes in working directory)                                                                                                                     
        modified:   file1.txt                                                                                                                                                               

no changes added to commit (use "git add" and/or "git commit -a")           
```


>[!alert] STASH
>the stash allows you to save unstage changes and to access these whenever you want to do

---
## many stashes
You can have a lot of different stashes
`git stash list` lists all stashes
```bash
$ git stash list                                                                             
stash@{0}: WIP on master: cbb881b first commit                                                                                                                                              
stash@{1}: WIP on master: cbb881b first commit 
```
you can go to the any of these stashes
```bash
$ git stash apply 1                                                                          
error: Your local changes to the following files would be overwritten by merge:                                                                                                             
        file1.txt                                                                                                                                                                           
Please commit your changes or stash them before you merge.                                                                                                                                  
Aborting                                         
```
It's not working, because you are in the normal git logic
If you want to access stash data, well you have to do simething with this data (stash again, add the changes and commit them, ...)
so:
1. `git stash` again (we will have three stashes) an now
2. `git stash apply 2`
```bash
$ git stash apply 2                                                                          
On branch master                                                                                                                                                                            
Changes not staged for commit:                                                                                                                                                              
  (use "git add <file>..." to update what will be committed)                                                                                                                                
  (use "git restore <file>..." to discard changes in working directory)                                                                                                                     
        modified:   file1.txt                                                                                                                                                               
  
no changes added to commit (use "git add" and/or "git commit -a")                                                                                                                           
(base) jarek@jarek-Lenovo-G700:~/PROG/Billennium/GIT/git_lern git a
```

to use the `stash` with message:
`git stash -m "some message"`
```bash
$ git stash push -m "third feature"                                                          
Saved working directory and index state On master: third feature 

$ git stash list                                                                             
stash@{0}: On master: third feature                                                                                                                                                         
stash@{1}: WIP on master: cbb881b first commit                                                                                                                                              
stash@{2}: WIP on master: cbb881b first commit                                                                                                                                              
stash@{3}: WIP on master: cbb881b first commit
```

----
## add a stash to the project
If you want to add one of these stashes to your main project:
`git stash pop [index]`
`git stash pop 0` add the latest stash to the main project
and then `git add .` -> `git commit -m "..."`
the added stash will be delete from the stash list
```bash
$ git stash pop 0                                                                            
On branch master                                                                                                                                                                            
Changes not staged for commit:                                                                                                                                                              
  (use "git add <file>..." to update what will be committed)                                                                                                                                
  (use "git restore <file>..." to discard changes in working directory)                                                                                                                     
        modified:   file1.txt                                                                                                                                                               
        
no changes added to commit (use "git add" and/or "git commit -a")                                                                                                                           
Dropped refs/stash@{0} (e4e4c8ec3a304116f4eb74ad7aa642c80897a816)    
```


----
## delete stash
to delete a stash from the list:
`git stash drop [index]`
`git stash drop 0` delete the latest stash

`git stash clear` delete all stashes




