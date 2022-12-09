[[_ Preface Git - Practical Guide]]
[[- Basics Version Management]]

---
# detached HEAD
We commited some changes
but now 
we want to change something in our before the last commit, 
so
`git checkout before_the_last_commit_ID`
```bash
git checkout 26e444e7106639c7eff412a4f59045eefaa6ab10`

You are in 'detached HEAD' state. 
...

HEAD is now at 26e444e second


$ git branch
* (HEAD detached at 26e444e)
  master

```

You changes content of one the staged file.
You added a new file
now `git add .`
next `git commit -m "changeges in deteach mode"`

now you come back to the master branch
```shell
$ git switch master

Warning: you are leaving 1 commit behind, not connected to
any of your branches:

  f3de53d changeges in deteach mode

If you want to keep it by creating a new branch, this may be a good time
to do so with:

 git branch <new-branch-name> f3de53d

Switched to branch 'master'

```

to save changes made in detached HEAD mode, you have to create a new branch:
` git branch detached-head f3de53d`

```shell
$ git branch
  detached-head
* master

$ git merge detached-head
Merge made by the 'ort' strategy.
 detached-head.txt | 0
 second-commit.txt | 1 +
 2 files changed, 1 insertion(+)
 create mode 100644 detached-head.txt

```

generaly
You are in detached HEAD mode (e.i. `git checkout 26e444`, you made changes (e.i. changed a content of the file)
1. create a new branch with
2. switch to the master branch
3. merge master with the new branch
4. delete useless branches `git branch -D branch_name`


















