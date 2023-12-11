#git/branch  #plurasight  #golightly_craig


---
# Working with Git Branches

`main`  will be use not `master`
`git config --global init.defaultBranch <name>`

`git branch -m <name>` the just-created branch can be renamed bia this command

in the master branch we have 1 commit, after we add two new files, and make some changes in the first file.

now we make **a new branch** named `quicfix`:
```shell
$ git checkout -b quicfix
Switched to a new branch 'quicfix'

```
and now we add and commit this changes.
and now we  lisl a folde and come back to master and list a folder:
```shell
$ ls
bug.txt  function1.txt  function2.txt
$ git checkout master
Switched to branch 'master'
$ ls
bug.txt
$ git checkout quicfix
Switched to branch 'quicfix'
$ ls
bug.txt  function1.txt  function2.txt
```


1. You create a master branch when you start the new work
2. You can create a new branch when you are starting something that you're not quite sure of 
3. If your code from 2 is partialy correct you can create another branch with a new solution and add your to this third branch


## demo

- create a branch to solve problem
	- commit hte first attempt
- create a second branch from main
	- commit partial solution
- go back to first branch to copy step

```shell
$ git init
$ vim experiment.txt
$ git add .
$ git commit -m "Demo setup"
[master (root-commit) 2202735] Demo setup
 1 file changed, 2 insertions(+)
 create mode 100644 experiment.txt
```
add a new branch
```shell
$ git checkout -b first-try
Switched to a new branch 'first-try'

```
we add some changes to the `experiment.txt` file
```shell
$ vim experiment.txt 
$ git add *
$ git commit -m "first attempt"
[first-try f861f50] first attempt
 1 file changed, 11 insertions(+)
jarek@jarek-Legion:~/0_PROG_bill/Git/plurasight/branches$ git checkout master
Switched to branch 'master'
```
these changes didn't work out, so we returned to the master branch and we will make a new branch:
```shell
$ git checkout -b second-try
Switched to a new branch 'second-try'
```
We make some changes in the file, but the file is without any changes made  on the branch `first-attempt`

```shell
$ git checkout -b second-try
Switched to a new branch 'second-try'
$ vim experiment.txt 
$ git add *
$ git commit -m "partial solution"
[second-try b2b62d0] partial solution
 1 file changed, 8 insertions(+)
$ git checkout first-try
Switched to branch 'first-try'
$ ls
experiment.txt
$ vim experiment.txt 
$ git checkout second-try 
Switched to branch 'second-try'
$ vim experiment.txt 
```

#git/checkout  #git/switch  
>[1important] commands
>`git branch` list your branches
>
>`git checkout <branch-name>` switch to work in a different branch
>`git switch <branch-name>` switch to work in a different branch
>`git checkout -b <new branch name> ` create a new branch and switch to that new one
>`git switch -c <new branch name> ` create a new branch and switch to that new one


## Dirty Branch
#dirty_branch








