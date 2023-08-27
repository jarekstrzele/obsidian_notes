[[_ The Ultimate Git Course]]


`git init`

to remove repo `rm -rf .git`

--------



---
# to see files

#### `git ls-files`  - to see files in the staging area

#### `git diff-tree --no-commit-id --name-only -r HEAD` to see files in the last commit 

#### `git status -s`
` M` modified (only in working directory)
`??` untracked
`A` added



the first/left column represents the staging area
the second/right represents the working directory


# WORKFLOW
1.  create a project and `.git`
2. you make some changes 
3. you add those changes to `staging area` (to review the project before the snapshots)
4. you make a commit those changes, it doesn't make the staging area empty; this commit contais:
	1. ID
	2. Message
	3. Date/time
	4. Author
	5. Complete snapshot

# example
- `git init`
- two new files will not be tracked (`echo some_text > filename.txt )
- `git add .` (the files are in the staging area)
- `git commit -m "some msg about the project changes"`


# commits
- messages not short not long
- commit often - *as you reach a state you want to record THEN make a commit*
	- one commit for bug fix, other for a new type
- use PRESENT `Fix the bug`

# skipping the staging area

`git commit -a -m "some msg"` or `git commit -am`
`-a` means all files


# How to remove a file
- you have a file2.txt
- `rm file2.txt`
- `ls` - there won't be `file2.txt`
- but `git ls-files` -show all files in the staging area,
- `git add file2.txt` - it removes the `file2.txt` from `staging area`
- 
### `git rm file2.txt` 
it removes `file2.txt` from ==the working area and from the staging area==

#### `git rm --cached file` rm file only from ==staging area==

There is a similar way to rename a file. Instead to make two step (rename + add), you can use:
#### `git mv old_name new_name`
`git commit -m "some msg"`

----
`.gitignore`
in git there are templates for different languages










