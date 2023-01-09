[[_W3school GIT]]

---

# Branch
#git/branch

>__branch__ is a new/separate version of the main repository

Branches allow you to work on different parts of a project without impacting the main branch.
Branch can be merged with the main project.


## New Git Branch
`git branch hello-world-images`   now we created a new branch called  "hello-world-images"

`git branch` ->
```bash
   hello-world-images
 * master 
```

`*` we are on the `master` branch 

## Switching between branches

`checkout` is the command used to check out a branch; moving us FROM the current branch, TO the one specified  at the end of the command

```shell
git checkout hello-world-images
// Switched to branch 'hello-world-images'
```

>Using the `-b` option on checkout will create a new branch, and move to it, if it does not exist


## Switching between branches
to change the branch:
`git checkout another_branch_name`
`git checkout master`

---


## MERGE
#git/merge 
### Emergency Branch
We found an error. We have two branches and we want to fix the error without interacting with these branches.
so
we create a new branch and changed to it:
```shell
git checkout -b emergency-fix
```

We fix the error.

### MERGE
We need to change to the master branch
`git checkout master`
#git/merge
Now we MERGE the current branch (master) with emergency-fix:
`git merge emergency-fix`

If no changes had been made to master while we were working, GIT sees this as a continuation of master; __"FAST_FORWARD"__ -> master and emergency-fix will be the same 
and we will can delete emergency-fix:

### TO DELETE the branch:
`git branch -d emergency-fix`







