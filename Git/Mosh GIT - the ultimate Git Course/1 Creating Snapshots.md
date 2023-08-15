[[_ The Ultimate Git Course]]


`git init`

to remove repo `rm -rf .git`

---
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





