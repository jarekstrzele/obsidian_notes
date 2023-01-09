[[_ Preface Git - Practical Guide]]


---

# Basics 
[[Basics - THEORY]]
[[Basics first step init, status]]
[[Basics - Branches & Commits]]
[[Basics - Delete]]
[[Basics - detached HEAD]]

----
# .gitignore
you have some files in your priject but they don't have to be a part of your version management

`.gitignore` created manualy 
which files and folders should be ignored by Git
in the `.gitignore`:
- `test.log` momentally this file will be ignored by Git
- `*.log` ignore all files with `log` extention

```gitignore
*.log
!test.log
web-app/*
```
- ignore all files with `.log` but `test.log` not ignore
- ignore folder `web-app` with all its files and subfolders 

---
# WRAP UP
## General
command | explanation
------- | -----------
`git --version` | check installed Git version
`git init` | create empty Git repository
`git status` | check working directory & staging  area status
`git log` | display all commits of current branch
`git ls-files` | list data in staging area

---
## Commit Creation & Access
command | explanation
---- | ----
`git add  filename` <br> `git add .`    |  add single file or <br> all WD files to staging area
`git commit -m "message"` | create <br> a new commit
`git checkout commit_id` | checkout commit <br> (detached head!)

---
## Branch Creation & Access
command | Git 2.23+ |explanation 
--- | --- | ---
`git branch branch_name` |?`git switch branch_name`| Create new branch
`git checkout branch_name` | |go to branch
`git checkout -b branch_name` | `git switch -c branch_name` | create and access new branch
`git merge other_branch` | | Bring other branch'a changes to current branch

 
----
## Deleting Data

repo status | command | explanation
:--- | :--- | :--- 
WD File <br> (is part of <br> previous commit) | `git rm filename` <br> `git add file_name` | Run command <br> after file was deleted <br> from WD
Unstaged <br> Changes | `git checkout (--) .` <br> (2.23) `git restore file_name` or `.` | Revert changes <br> in tracked files
   Unstaged <br> Changes | `git clean -df` | Delete untracked files
   Staged <br> Changes | `git reset file_name & git checkout -- filename` <br> `git restore --staged file_name` or `.` | Remove file(s) <br> from stagin area
Latest <br> commit(s) | `git reset HEAD~1` `git reset --soft HEAD~1` <br> `git reset --hard HEAD ~1` | UNDO latest (~1) commit
branches | `git branch -D branch_name` | delete branch















