[[- Basics Version Management]]

[[Basics - THEORY]]
[[Basics - Branches & Commits]]


---
# First step
`git [command]`
`git status`

`git init` we transform our project folder into the git working directory

## add to the staging area
`git add [what]`
`what` file names, `.` all files
`git add .`

## commit
first you have to
```bash
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```

than you can:
```bash
$ git commit -m "add first commit"
[master (root-commit) 1468b87] add first commit
 1 file changed, 1 insertion(+)
 create mode 100644 initial-commit.txt

```


## log
`git log` 
```bash
$ git log
commit 1468b87c9197f5aaf7dda3c0f95e8d8f26667c39 (HEAD -> master)
Author: Jarosław Strzelecki <js100code@gmail.com>
Date:   Mon May 23 21:08:01 2022 +0200

    add first commit
```

We add a new file to our working directory, so we have to add this file to repository:
`$ git add second-commit.txt `

`git log` -> you see commit ids, so you can:
`git checkout commit_id` 

If you write `git checkout second_commit_Id`, you pass to only the first commit (the second one will disapear)
`git checkout branch_name`
`git checkout master` -> you will return to the state with the second commit

















