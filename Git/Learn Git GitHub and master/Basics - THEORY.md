[[- Basics Version Management]]

[[Basics first step init, status]]
[[Basics - Branches & Commits]]



---
# Theory

> GIT tracks changes, GIT doesn't save all files!!

## commit

- We have a `Web Shop` app (folder: index.html, style.css, images)
- we out to transform this folder into ==working directory== (all project files, which are part of this folder will be managed by ==Git==) (`git init`) after `commit`
	- `git init` creates ahidden folder `.git` REPOSITORY:
		- ==Staging Area== (Index File)
		- ==Commits== (Objects Folder)
- `commit` will create a "snapshot 1" (se store the initial stage of our project)
- we make some changes in our css file, then we `commit` -> we make "snapshot 2"

![[git-commit-model.excalidraw|500]]

---
## branch
#git/branch 
> Git stores all ==commits== you make in the so-called master ==branch==

**working directory** = **Tree** = folder with subfolder and files of our project

### master branch
- a new Git project -> add your files at different commits  -> all these commits will be stored inside the so-called MASTER BRANCH
- **master branch** contains *commit 1*, *commit 2*, ... (you have ==an entire history== of the project

### new branch
- with ==branches== we can create a "new" working directory/tree which is an entire copy of the current state of your master branch 
- this new branch contains all previous commits, but now you can work independently from that master branch (new `add` , new `commit`)
- you can add these changes back to the master branch ( `merge`)



---
## Repository `.git`
- Staging Area (Index File)
	- `add`
	- a draft area
	- "Hey Git, these changes made to this file(s) should be part of the next commit "
- Commits (Objects Folder)
	- after add(s) you can make `commit`
	- a snapshot of our project

> ==GIT = Tracking changes - NOT storing files again and again







