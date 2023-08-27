#plurasight #git #beginner #perrotta_paolo

# Git: The Big Picture

## Getting to know Git
> [!git]
> an open source distributed version control system
> - tracks changes to source code
> - IS NOT a backup

`git init` put this project under Git (a repository will be created)
`git add .`  put all the project files in the index
`git commit -m "[msg]"` create a snapshot that includes all the files in the index

`git log` show the history of the project
`git status`

**What changed between two snapshots?**
`git diff [commit_id] [commit_id` show the difference between snapshots

### time travel
#git/checkout 
`git checkout [commit_id]` 
	- hey Git, take me back in time to this version `[commit_id]` of project
	- it takes the version of the  project that we want to go to

----
## Understanding Version Control
==Tracking your project's history== is the **first** and most obivous reason to use version control

### branching - manage multiple versions of a project
**the second**
==managing multiple version of a Project==
e.g. app + premium app -> easy thanks to `branching`
#git/switch 
`git switch [branch_name]` you move to the `[branch name]`

### merging
#git/merge 
`merge` is a counterpart/copy/duplicate to branching
e.g.
	- you have two branch `main` and `premium`
	- you want to add some changes in `main` to `premium`
	- go to `premium` and execute `git merge main`
		- now the history of the `premium` branch includes everything (main commits + premium commits) 
		- the history of `main` includes only itself commits


### sharing code amongst developers
> if it hurts, do it more often
> Martin Fowler

==Git allows to frequently do small integration==
It makes much easier to integrate code


### Coordinating teamwork
not just developers but all others people and apps (e.g. Jenkins)

----
## Making Sens of Git

- Git is fast
- Git is smart
- Git is flexible
- Git is safe
- Git is ==DISTRIBUTED version control==

### client-server version control
e.g. *Subversion*

workflow:
1. copy files from server to your local computer
2. make some changes
3. copy files from serve to your local computer and merge your changes with the latest version of project
4. push files to the server

### distributed version control
workflow:
1. `git clone ...` copy all repo (files+history with the latest commit) (`ls -a` show me the content of the current folder including the hidden files and directories `.git`)
2. now you can change every thing in your local repo; 
	1. and this repo has a link to the shared repo-> it is called ==remote== 
	2. to get the latest commits from the remote repo -> `git pull` (from remote to local)
	3. `git push` from local to remote
3. you can work on your local repo even if you have no internet connect

GIT is:
- Not ideal for binary files
- not user-friendly

> 
> Git is hard to learn but easy to use
> 

-------
## The Git Ecosystem
### github
#git/fork

GitHub is:
- a hosting service
- a set of project management tools
- a social network centered on coding
- a workflow
	- this is the open source workflow
	- e.g.
		- a man asks GitHub to give him a remote clone from a other GitHub project (e.g. `plurasight/aaa`)
		- this operation is called ==the fork==, the man has on his own copy of this project  (`nusco/aaa`)
		- the man makes some changes on his repo
		- the man sends a changes request to the plurasight
		- if user plurasight accept the changes, he pull this changes to his own repo





















