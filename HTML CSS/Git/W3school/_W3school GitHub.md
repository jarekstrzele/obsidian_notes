
# GITHUB
1. Create an account on GitHub
2. Create a new repository (np. "hello-world", public)

Since we have already set up a local Git repo, we are going to push that to GitHub:

1. From GItHub copy a link "https://..../hello-world/git"
2. Past this link `git remote add origin https://github.com/w3schools-test/hello-world.git`

`git remote add origin URL`:
- you add a remote repository,
- with the specified URL
- as an origin to your local Git repo

3. Push your master branch to the origin url, and set it as the default remote branch
`git push --set-upstream origin master`

GitHub has a very good code editor.

---

# Git Pull from GitHub
#git/pull
Any time you start working on a project, you should get the most recent changes to your local copy.
You can do that witj `pull`.

`pull` is a combination of 2 different commands:
- `fetch`
- `merge`

## Git Fetch
#git/fetch
`fetch` gets all the change history of a tracked branch/repo
`git fetch origin` on your local Git -> fetch updates

`git diff origin/master`  will show the differences between our local master and aorigin/master


## Git merge
`merge` combines the current branch, with a specified branch.


---
## GIT Push
You make same changes to our local git and you push them to GitHub

`git push origin`


---
## Git GitHub Branch
click "master" branch, there you can create a new branch

`Preview changes` click that to see the changes you made

`commit changes`

---
## Pulling a branch from hitHub

`git pull` 

---

`git branch -a` you see all local and remote branches
`git branch -r` you see only remote branches
 

---

## Push a branch to GitHub
a new local branch push to GitHub

`git push origin update-readme` push the branch from local branch to GitHub



