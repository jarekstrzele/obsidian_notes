[[- Basics Version Management]]

[[Basics - THEORY]]
[[Basics first step init, status]]

---
# Branches
#git/branch 
We have Working Directory with some files and folder
and we have three commits on the baster branch
==master branch== is the first branch you create in Git projects

We can make a copy of all project, add some new folders and files (new features), add new commits (this branch will be called for example "Landing-Page Branch")

`git branch` to get overview of all the branches you have in your current project 

### to create
`git branch branch_name` to create a new branch

### to switch
`git checkout branch_name `
`git checkout master`
`git checkout second_branch`

### to create and switch
`git checkout -b new_branch_name`


### to merge branches
`git merge branch_name-from_which_data_will_be taken`
I am on the `master branch` and I want to merge with the `third_branch`, so:
`git merge third_branch`


## What is "HEAD"
#git/head

we have a *master branch* with three commits:
 - c1
 - c2
 - c3 <- this is a HEAD, the latest commit (that behavour by default)

(when we are checking our branches out we are referring to a specific branch  with with its last commit)

we have an other branch *new_bb*, that branch has four commits, so c4 is its head
```bash
commit 918dd09b181db3d8e0f613c0e74ca218602211e9 (HEAD -> master, new_bb)

$ git checkout new_bb
commit 918dd09b181db3d8e0f613c0e74ca218602211e9 (HEAD -> new_bb, master)

```

## "Detached" HEAD
```bash
$ git branch
* master
  new_bb

$ git log
commit 918dd09b181db3d8e0f613c0e74ca218602211e9 (HEAD -> master, new_bb)
Author: Jarosław Strzelecki <js100code@gmail.com>
Date:   Wed May 25 20:13:32 2022 +0200

    third commit

commit 26e444e7106639c7eff412a4f59045eefaa6ab10
Author: Jarosław Strzelecki <js100code@gmail.com>
Date:   Wed May 25 20:12:00 2022 +0200

    second

commit de110b81a75d89a3ad746f230b46a1836b2af7c6
Author: Jarosław Strzelecki <js100code@gmail.com>
Date:   Wed May 25 20:10:53 2022 +0200

    first

```

I am checking the second commit out
```bash
$ git checkout 26e444e7106639c7eff412a4f59045eefaa6ab10

Note: switching to '26e444e7106639c7eff412a4f59045eefaa6ab10'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

....

$ git branch
* (HEAD detached at 26e444e)
  master
  new_bb


```

```bash
$ git checkout master
Previous HEAD position was 26e444e second
Switched to branch 'master'

$ git branch
* master
  new_bb

```

----
# Branches & "git switch"
#git/switch
from git version 2.23 we have some new commands

`git switch` allows you to do :
		- switch branches 
		- and create new branches

(confusing: `checkout` for commits and for branches)

### to switch branch
`git switch branch_name`

### to create a new branch
`git switch -c name_of_new_branch`


----
# Commits










