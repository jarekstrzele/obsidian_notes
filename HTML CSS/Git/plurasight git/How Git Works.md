#git #plurasight  #perrotta_paolo 

---
# How Git Works

> [!important]
> If you want to master Git, don't worry about learning the commands.
> Instead, learn the model.

git old and new one:
- to move to an other branch: 
	- (old) `git checkout` 
	- (new) `git switch`

## Git is not what you think
### a metaphor: Git is an onion
> [!`man git`]
> git - the stupid content tracker

git is:  
	- a distributed version control system > 
		- a version control system >
			- the stupid content tracker >
				- (forget about a file tracker, a notion of a commit, version) BASIC IDEA behind Git: ==Git is map==
> [!the core of Git]
> ==Git is just a map!!!==
> 	- a simple structure that maps keys to values
> 	- is persistent; it's stored on your disk


### Git is a map 
**values** are just sequences of bytes (e.g. the content of a text file)
You can give a value to Git and it will calculate (with an algorithm SHA-1) a **key** for it, a ==hash==
e.g.  
	value: "Apple Pie" -- Git calculate a hash --> 
	key: e393909238a039238c9820x87362fe382790cbe5
	(20 bytes in hexadeciumal format -> it is a sequence of 40 hex digits)
```shell
$ echo "Apple Pie" | git hash-object --stdin
23991897e13e47ed0adb91a0082c31c82fe0cbe5

```
If you pass the same sequence of bytes to hash-object, then you get the exact same hash every time on every operating system

>
> Every object in Git has its own SHA1!!!!!!!!
> SHA1s are unique in the universe
> 

```shell
$ echo "apple Pie" | git hash-object --stdin
b6723f8b4c6b726db1c8dae6ebfc1596f8f05f8c
$ echo "apple pie" | git hash-object --stdin
124b2c537cbdf63a0c8b88d409b3b0882b9b3996
$ echo "apple pie " | git hash-object --stdin
c693a766af69ec3075bf27b4c47be16b28936aab

```


### Git is a persistent
```shell
$ echo "Apple Pie" | git hash-object --stdin -w
fatal: not a git repository (or any of the parent directories): .git
```
`-w`  to write text into a Git repo
but in this folder there is no repo
so
```shell
$ git init
$ echo "Apple Pie" | git hash-object --stdin -w
23991897e13e47ed0adb91a0082c31c82fe0cbe5

```
now "Apple Pie" is save in the Git repo in the subfolder `.git/objects` (this is called the object database)
in this folder there is a `23` subfolder with file 991897...
23 and 9918... are digits -> This is what Git calls a blob of data
> blob is a generic piece of content

to read this file:
`git cat-file 23991897e13e47ed0adb91a0082c31c82fe0cbe5 -p`
`-t` show type
`-p` print

### Git is a stupid Content Tracker
#git/commit 
> [!commit]
> - It's a simple and very short piece of text, nothing else
> - You can see commit by:
> `git cat-file -p [commit_id]`
> - The commit text contains:
> 	- all the metadata about the commit
> 		- the name of the author
> 		- the committer
> 		- the data of the commit
> 		- msg
> 	- and the hash tree
> 		- a tree is a directory stored in Git
> 			- is a tiny piece of text
> 			- contains a list of the content of the directory (list of hashes)
> 		- a blob is the content of file stored in Git
> - the commit is pointing at the root directory of the project
> ==Commits are linked (the parent is the previous commit)==

tree <-> content of a folder
blob <-> content of a file (the same content the same hash)


### Git is a version control

A new commit -> a new root directory (a new hash)
but
(supose we changed a file but not a folder)
new commit contains:
- info about parent
- tree (the subfolder wasn't changed, so it has a old hash)
- blob (the file was changed, so it has a new hash)

`git count-objects` -> show how many objects are in the `folder objects`

> [!remember]
> each 
> 		- commit, 
> 		- blob, 
> 		- tree
> are just files

there is another type of object
>[!an annotated tag]
> it is a small object in the database that contains the data, the message, author, ... 
> and
> points to a commit


GIT IS A HIGH-LEVEL FILE SYSTEM BUILT ON TOP OF YOUR NATIVE FILE SYSTEM!!!!!!! 
==It is a version file system, because it has commit.==

-------------
## Branches Demystified

#git/branch 

`git branch` show current branch ?

> 
> ==Git puts branches into directory calles `refs`==
> 

```shell
$ cat .git/refs/heads/main
14b86af6044a8b7a5ba9a6f56dbdf13c365136c5
```
This is a hash of the current commit.
```shell
$ git log
commit 14b86af6044a8b7a5ba9a6f56dbdf13c365136c5 (HEAD -> main)
Author: Jarosław Strzelecki <js100code@gmail.com>
Date:   Tue Aug 2 21:57:41 2022 +0200

    Add apple.pie.txt

commit 1af5a7dde1e742ee4ce011d685d74bd16bce5536
Author: Jarosław Strzelecki <js100code@gmail.com>
Date:   Tue Aug 2 21:56:49 2022 +0200

    first

```

>[!BRANCH]
>it is just a reference to a commit

**create a new branch**
`git branch branch_name`
```shell
$ git branch ideas
$ git branch
  ideas
* main
```

In the `.git/refs/heads` Git has just created a new file `ideas`
```shell
$ cat .git/refs/heads/ideas
14b86af6044a8b7a5ba9a6f56dbdf13c365136c5

```
Now we have two commits, two branches
and
the branches are pointing at the same commit

>[!HEAD]
>	it is a reference to a branch
>	A branch is a reference to a commit
>	so
>	Head is a pointer to a pointer
```shell
$ git branch
  ideas
* main
$ cat .git/HEAD
ref: refs/heads/main
```

We have just added a content of `apple.pie`
```shell
$ tree
.
├── menu.txt
└── recipes
    ├── apple.pie.txt
    └── README.txt

1 directory, 3 files
```
`git add`
`git commit`  -> Git create a new object/commit and the commit has the previous commit as a parent -> and move head and main to new commit
Now we have three commits.
```shell
$ git switch ideas
Switched to branch 'ideas'
$ git branch
* ideas
  main
```
#git/switch  
-> Git makes that HEAD point to ideas
```shell
$ cat .git/HEAD
ref: refs/heads/ideas

```
After the switch our working area changed to the content of the commit pointed ar by ideas

>[!switch]
>move HEAD and update the working area

We change the content of `apple.py.txt` (it also has a tablespoon of cinnamon)

We commit our changes, so branch "ideas" points to a new commit and "HEAD" point to this branch

### Let's Merge!
You have file `recipes/apple.pie.txt` with different content on branches (main, ideas).
You are on the main branch.
You try to merge:
```shell
$ git merge ideas
Auto-merging recipes/apple.pie.txt
CONFLICT (content): Merge conflict in recipes/apple.pie.txt
Automatic merge failed; fix conflicts and then commit the result.

```
so
edit the file and fix the conflict
`git add file`
`git commit` (Git automatically generate a message)
```shell
$ git commit
[main 109edef] Merge branch 'ideas'

```


>[!MERGE]
>It is just a commit, with one exception, it has TWO PARENTS
```shell
$ git cat-file -p 109ede
tree a9ad2f38ee41d03ce1de5f4f08913c43380c3f72
parent 4890e894ea7ddce9896bb0d6601f8cd21f531364
parent 9a708aa3a4ca9654fa797203f58f9ef690e0c3fc
author Jarosław Strzelecki <js100code@gmail.com> 1659513128 +0200
committer Jarosław Strzelecki <js100code@gmail.com> 1659513128 +0200

Merge branch 'ideas'

```

----
### Time travel for developers
Objects in the database are:
- commits
- blobs
- trees
- tags

There are references each other.
##### ==References between commits are used to track history!!==
**All the other references are used to track content**

### Merging without merging
#git/fast-forward 
You have two branches `main` and `ideas`.
`Main` contains the lastest version of recipes.
You swich to `ideas` branch.
```shell
$ git merge main
Updating 9a708aa..109edef
Fast-forward
 recipes/apple.pie.txt | 1 -
 1 file changed, 1 deletion(-)
```
Git merges the ideas with main `Fast-forward` (It doesn't create a new commit but only moves `ideas` to the latest commit) (remember that a branch is only the reference to a commit, so the `ideas` branch will be point to the latest commit)


### Losing Your HEAD
You can checkout a commit.
`git checkout id_commit`

Now HEAD points directly to commit, so
```shell
$ git branch
* (HEAD detached at 109edef)
  ideas
  main

```
If you make some commits, they won't be saved if you return to a branch.
so
If you want to save them, create a new branch (put a branch on it) `git branch name_of_new_branch`


### RECAP
- a Git repository is a bunch of objects linked to each other in a graph
- objects: commits, blobs, trees, tags
- branches are references to commits
- a HEAD is a reference, 
	- it marks our current position in the graph,
	- it usually pointing to a branch 
	- it could be detached and pointing directly to a commit

==RULES==:
- the current branch tracks new commits
- when you move to another commit, Git updates your working directory
- unreachable objects are garbage collected

----------
## Rebasing Made Simple
#git/rebase

You have to branches: `main` and `spaghetti` without any conflict, so you can `git merge main` or `got merge spaghetti`, but you can also REBASE
You are on the `spaghetti` branch, so:
#### `git rebase main` 
this command:
- finds a commit shared by `main` and `spaghetti`
- detaches the `spaghetti` branch from this commit
- moves this detached branch on top of `main`, so it changes the base of this branch

and if you do:
- `git switch main`
- `git rebase spaghetti`
Git makes Fast-forward rebasement (it moves `main`  to the same commit that `spaghetti` points)

>[!important]
>- objects in database are immutable
>- so `rebase` makes new commits (copies of commits but parents are different; and a new content -> a new hash, so `rebase` has to make new commits)
>- and `rebase` makes that the branch points to the new commmit

Old commits are not accessible (almost), so Git will eventually garbage collect them.

MERGES PRESERVE HISTORY (but the project history can be complicated)

REBASES REFACTOR HISTORY (but the project history became simpler)

## ==When in doubt, just merge!!!! ==

---
## Tags in Brief
#git/tag

>[!TAG]
>- It is like a label for commit
>- It is in `.git/refs/tags`
>- It is made of two parts:
>	- first: it is a branch-like thing (a reference)
>	- second: the reference points to a database object of type tag (which points to a commit)
>- A tag is like a branch that doesn't move

**"Lightweight Tag"** (It just points to a commit)
`git tag release_1`

**Annotated Tags** (it is a branch-like object that points to a tag object that points to a commit)
`git tag release_1 -a -m "First release, still unstable"`

to list tags:
`git tag`

If you want ot move back to the commit with this tag:
`git checkout release_1`

```shell
$ cat .git/refs/tags/release_1
1353f19736b354279eba54454549b4f3516f749f
$ git cat-file -t 1353f19736b354279eba54454549b4f3516f749f
tag
$ git cat-file -p 1353f19736b354279eba54454549b4f3516f749f
object 9dc0d2dbc138dc1992c6d4478fb2985cdccb441c
type commit
tag release_1
tagger Jarosław Strzelecki <js100code@gmail.com> 1660211175 +0200

First release, still unstable


```

------------------
# Distributed Version Control

`git clone ....` (both computers (locale and remote/cloud/GitHub) contain the whole project abd its history ) ==All of these clones are peers !!!!!! ==


## Local and Remote
1. You have a repo on GitHub
2. You clone this repo on your local computer -> Git add some extra configurations `./git/config`
**a git repo only local:**
```
  1 [core]
  2         repositoryformatversion = 0
  3         filemode = true
  4         bare = false
  5         logallrefupdates = true

```

**a git repo local and remote**
``` 
  1 [core]
  2         repositoryformatversion = 0
  3         filemode = true
  4         bare = false
  5         logallrefupdates = true
  6 [remote "origin"]
  7         url = https://github.com/jarekStrzelecki/wired-brain-recipes.git
  8         fetch = +refs/heads/*:refs/remotes/origin/*
  9 [branch "master"]
 10         remote = origin
 11         merge = refs/heads/master
```
This repo can remember information about other copies of the same repo. Each other copy is called `a remote`.
When you clone the project, Git immediately defines a default remote and calls it with a conventional name - ORIGIN
`git branch`
`git branch --all`
```shell
$ git branch
* master
  new_branch

$ git branch --all
* master
  new_branch
  remotes/origin/master

```

`refs>remotes>origin`

> Like a local branch, a remote branch is just a referenc to a commit

both branches point to the same commit
```shell
$ git show-ref master
86a77622be805ce11269244839a4bc9c0b555941 refs/heads/master
86a77622be805ce11269244839a4bc9c0b555941 refs/remotes/origin/master

```

## The joy of pushing
`git push` from local to remote


## The Chore of pulling
1. one repo on GitHub and one locally
2. You changed the local repo
3. Somebody changed the remote repo.
4. You want to push your changes? -> conflit!!, so you have two option:
	1. `git push -f` (force push - not recommended; my local changes are important, so GitHub override remote changes by you changes
	2. ==better one== solve confilct on your local machine `FETCH->MERGE->PUSH` -- reduce to -> `PULL->PUSH`
		1. first you need to fech the data from the remote `git fetch` 
		2. `merge` your branch with the fetched branch from the remote repo (solve conflicts) (merge never rewriting history)
		3. now you can push your repo to the remote repo


## rebase revisited

>[!rule]
>Never rebase shared commits
>


## Two GitHub Feature
### Fork
It is kind of like a clone, but it's a remote clone (you clone somebody project from GitHub to your GiHub.  And you clone that one on your local machine (Git automatically creates a remote in our local repo, pointing at origin)

If you want to connect your local fork project with original use `upstream` (we can pull changes from the origin one to our local fork) and the you can push the local to your origin

`pull request` you have to send it to the original project on GitHub, to have access to make changes on the original GitHub project



















