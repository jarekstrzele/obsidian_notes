#javascript #udemy #stashchuk_bogdan 

---
# Start JS Bible
VC Code:
- Live server
- Prettier ()
- bracket pair color
- material
- 

## git
`git config --global user.name`
`git status`
`git add .`
`git commit -m "some msg" .`
`git init`
`git checkout commit_id`
 > When you checkout specific commit you will be in "detached HEAD" state and if you commit anything in this state and then chackout "master" branch, those commits made in "detached HEAD" state will be lost.
 >   Such commits are usually called "experimental"
 >   
`git checkout master`
`git log`

**head** a simply pointer to specific commits
**master** a simplu pointer to  specific commits

### branch
If you want to have separate version of your project, you should use ==BRANCHES==
#git/branch 
`git branch` -> list of all branches 
**branches** different versions of your project

`git checkout -b "name_of_new_branch"` -> generate a new branch and switch to it
```shell
$ git branch
* Branch1
  master
```
`git checkout master` return to the master branch
`git checkout Branch1` switch to the Branch1 branch

## clone repo
#git/clone 
`git clone 'httm_form_github'`

`git branch -r` -> show branches located in the remote repo
`git checkout --track name_of_the_branch` -> you will be able to use this remote branch on you local computer











