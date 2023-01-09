#plurasight  #git #stewart_aaron

# Getting Started with Git 2

Git is Version Control System - VCS:
- software designed to record changes made to files over time
- ability to revert back to a previous file version or project version
- compare changes made to files from one version to antoher
- version control any plain text file, not just source code


## analogy with coffe shop

==Three stages of a file==:
- **committed**
	- a file safely stored in a local db
- **modified**
	- if the file was changed, its status will be modified (so it is different than this one in a local db)
- **staged**
	- the  modified file saved in the staging area
	- these changes will be save in the next commit
	- if a file should be tacked, it has to be in the staged status


==Three states of a Git Project==
- **WORKING DIRECTORY**
	- a single copy
	- a checkout of one version of the project
	- Changes to files since the last chackout have not yet been added to the staging area for commit
- **STAGING AREA (Index)**
	- this area is between the working directory and the repo
	- it is used to build up a change or set of changes
	- prepared file to commit (what is committed is only what is currently in the staging area)
	- Files  in this state have been modified and added to be staged in the next commit snapshot
- `.git` directory (**REPOSITORY**)
	- this is the origin of the project's data
	- this is what is pull down from a remote server
	- Files in this state are committed and recorded to the project as version snapshots

#### commands
`pwd` Print working directory
`cd` Change working directory
`touch` create a new empty file (`copy con` for windows users)

`sudo apt install git`
`https://git-scm.com/download/win` git + Git Bash


#### configure
`git --version`
`git config --global user.name "Steve Jones"`
`git config --global user.email "jjj.ss@wp.pl"`


### example
1. create a local repo
2. create a project on Github
3. create a file in working directory
4. make `git add .`
5. make `$ git remote add origin https://github.com/jarekStrzelecki/wired-brain-recipes.git`:
	1. this command adds the origin GitHub repo to our local repo by createing a link that allows us to push and pull changes bewtween the two (local and remote)
6. `git push -u origin master` (send the local project to GitHub) (see [[ogólne]])
PAT: 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

`git help`
`man git`

----
## Basic Commands of Everyday git

## `git status`
>[!**branch**]
>it is a lightweight movable pointer to your project at a specific point in time

### `git status -s`
`git status --short`
`M` = Modified
`A` = New File added to staging area
`??` = New File added to staging area
`MM` the file was modified and added to staging area and after that was modified


### File stages

Committed | Modified | Staged | Untracked
--- | --- | --- | ---
Unmodified changes from the last commit snapshot | Changes made to files since last commit snapshot | Changes marked to be added into the next commit snapshot | Git sees a new file that didn't exist in our last commit snapshot


### Track a New File
`git add newFile`


### `git diff`
It responses to two questions:
1. What changes have I staged that are ready to be committed?
2. What changes have I made but not yet staged?

`git diff --staged` compares our staged changes to our last commit snapshot

### `git commit`

`git commit -a` skip a staging area and add all changes to the repo

`git commit -m "messsage"`


---------
## Extended Commands of Every day Git

### `git push`

```bash
$ git push origin master
Username for 'https://github.com': jarekStrzelecki
Password for 'https://jarekStrzelecki@github.com': 
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 8 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 456 bytes | 456.00 KiB/s, done.
Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/jarekStrzelecki/wired-brain-recipes.git
   f451f6b..95d7b05  master -> master

```
Instead of password pass PAT


### Check Commit History
`git log`
`git log -1` the latest commit
```shell
$ git log --oneline
95d7b05 (HEAD -> master, origin/master) add new vendor
f451f6b first commit

```

```shell
$ git log --stat
commit 95d7b057388711cc03ce34754952718414e4c4f7 (HEAD -> master, origin/master)
Author: Jarosław Strzelecki <js100code@gmail.com>
Date:   Tue Aug 9 12:28:37 2022 +0200

    add new vendor

 README.md   | 3 +++
 vendors.txt | 3 +++
 2 files changed, 6 insertions(+)

commit f451f6b2b102157cfd86090eb91657727f9c6e36
Author: Jarosław Strzelecki <js100code@gmail.com>
Date:   Mon Aug 8 12:34:04 2022 +0200

    first commit

 README.md | 1 +
 1 file changed, 1 insertion(+)

```


FULL information `git log --patch`

### Commit Messages
#git/commit 
Chris Beams wrote a great blog post in 2014 about writing commit messages that outlined the general seven rules to a great commit msgs.
<iframe src="http://chris.beams.io/posts/git-commit"  width="700" height="500"> </iframe>

 
---
### Remove and Move Files
You have a file (`f1.txt`) tracked by Git. You want to remove this file from the project.

#git/rm

1. Tell Git to stop tracking the file (`git rm filename`)
```shell
$ git rm new.txt
rm 'new.txt' // we have staged this file removal and Git stopped tracking this file
```
2. `git status` -> `deleted: new.txt`
3. `ls` -> our delete file is no longer at the list

`git rm --cached filename` -> Git will stop tracking this file but won't remove it.

#git/mv
**rename**
`git mv currentFileName newFileName`

==to save all these changes in the project you have to commit them!!!!!!!!==

----
### Branches
#git/branch 

http://git-school.github.io/visualizing-git

>[!a branch in Git]
>It is simply a lightweight movable pointer to a commit made in a project

**to create a branch**
`git checkout -b new_branch`
`-b` create a new branch and checkout to it (`HEAD` will point to `new_branch`)

>[!HEAD]
>It is just a pointer to our current state on the branch we are on

Make some commits on your new branch.
`git checkout master` -> return to the master branch (`HEAD` will point to the master branch). If you make some commits, they will be only on master branch

#### `git stash` (chować potem)
#git/stash
In one branch a have a file.
I added it to the staging area.
```shell
$ git stash
Saved working directory and index state WIP on new_branch: fa7592d rename, remove on new branch
$ git status
On branch new_branch
nothing to commit, working tree clean
$ git stash list
stash@{0}: WIP on new_branch: fa7592d rename, remove on new branch
$ git stash show
 aa.txt | 5 +++++
 1 file changed, 5 insertions(+)

```

to get this change out of stash `git stash pop` (the change would be dropped back into the working directory)


#### `git reset`
#git/reset
You change your history.
It allows us to move commits from history back into our working or stagin area
==BE CAREFUL!!!!!!!!==

`git reser --soft commitID` move this specific commit or commits back into your staging area from git repo
This is helpful if you want to regroup these changes into different commits or add more changes before committing.

`git reset --mixed commitID`  or `git reset` it moves the changes back to the working directory
`git reset --mixed 95d7b05`

`git reset --hard` it moves the changes to the trash (delete all changes from the git repo and the staging area/index)





