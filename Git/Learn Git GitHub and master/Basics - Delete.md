[[_ Preface Git - Practical Guide]]

[[- Basics Version Management]]
[[Basics - Branches & Commits]]

----
# DELETE
###### to check which files are currently part of our staging area:
`git ls-files`

I can just delete a file (third-commit.txt), but it's still on the straging area.
I have:
`git rm third-commit.txt`
or `git add third-commit.txt`

so now I can commit

----
# Undoing UNSTAGED Changes
You made some changes in a file, but you didn't make `git add`
You can undo these changes by `git checkout file_name.txt`

> `git checkout .` go back to the heads statues of all commits of all tracked files I have in my current branch

==a new command to do the same==
> `git resotre file_name.---` or
> `git restore .` for all possible changes in all files


## deleting file added to the working directory but not added to the staging area

`git clean -d [WHAT]` delete all untracked directories and files
`-d` delete 
`-dn` list all entries before deleting
`-df` deletet force with any futer questions

---
# Undoing STAGED changes
You have a file in the stagging area. You made some changes in the file. but you want to undo these changes.

**old way**
1. `git reset filename`
	- e.i. `git restet init-commit.txt`
	- `git reset` copies the latest stage of this file, so now file is not modified 
2. `git checkout filename`
	- `git checkout init-commit.txt`

**new way**
1. `git restore --staged filename`
2. `git checkout filename`

----
# Deleting Commits with `git reset`

**SOFT**
`git reset --soft HEAD~<how many commits back>`
`git reset --soft HEAD~1` => the last commit will disapear, 
but
our staging area rests intact by this command
- remove the commit


**DEFAULT**:
`git reset HEAD~1` => the last commit is deleted and the staging area is changed 
- remove the commit
- remove the changes from the staging area

**HARD**
`git reset --hard HEAD~1`=>
- remove the commit
- remove the changes from the staging area
- remove the changes from the working directory


----
# Delete Branches
`git branch -D branch_name`

`-d` deletes merged branches
`-D` deletes every branches (FORCE)
 
```bash
$ git branch -D new_bb
Deleted branch new_bb (was 918dd09).

```



























