[[_W3school GIT]]


---
# Adding New Files

- __tracked__ files that Git knows about and are added to the repository
- __untracked__ files tha are in your working direcotry, but not added to the repository

---
## Staging environment
#git/stage

__staged__ files are files that are ready to be __committed__ to the repository you are working on

`git add index.html`

## Add more than one file
`README.md` describes the repository

`git add --all`
`git add -A`
It will stage all changes (new, modified, deleted) files.

---
## Git commit
#git/commit 
Adding commits keep track of our progress and canges as we workk.
Git considers each __commit__ change point or "save point".

>When we commit, we should always include a message.

`git commit -m "clear message to see what has changed and when"`


TO S K I P the staging environment:
`-a`
`git status`
`git status --short`
	`??` Untracked files
	`A` Files added to stage
	`M` Modified files
	`D` deleted files
`git commit -a -m "some info"`

---
## Git Commit Log
To view the history of commits for a repository, you can use the `log` commang




