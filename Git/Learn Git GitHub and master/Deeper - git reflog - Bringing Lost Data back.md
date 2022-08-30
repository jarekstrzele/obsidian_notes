
[[- Diving Deeper into Git]]


----
# Bringing Lost Data back with `git reflog`
#git/reflog
>[!reflog]
>stores all our changes we made in our git project (by 30 days)

You add a new file, you `add .` and  `commit`.
You can delete the last commit (and this new file):
		`git reset --hard HEAD~1`
		

```bash
$ git reflog                                |  3 
526a6b5 (HEAD -> master) HEAD@{0}: reset: moving to HEAD~1                                               
972ae54 HEAD@{1}: commit: fiel2 added                                                                    
526a6b5 (HEAD -> master) HEAD@{2}: commit: add featre 3 to project                                       
cbb881b HEAD@{3}: reset: moving to HEAD                                                                  
cbb881b HEAD@{4}: reset: moving to HEAD                                                                  
cbb881b HEAD@{5}: reset: moving to HEAD                                                                  
cbb881b HEAD@{6}: reset: moving to HEAD                                                                  
cbb881b HEAD@{7}: reset: moving to HEAD                                                                 
cbb881b HEAD@{8}: commit (initial): first commit               
```

and now, if you write:
`got reset --hard 972ae54 `
you return to the commit you have just deleted
`972ae54` is a hash of this commit

---
## with a new branch
1. create a new branch `git checkout -b feature`
2. add a new file (add, commit)
3. return to master branch
4. delete the second branch () `git branch -D feature `
5. RECREATE a branch                 
```
$ git reflog
972ae54 (HEAD -> master) HEAD@{0}: checkout: moving from feature to master                  
a82f0c9 HEAD@{1}: commit: add file3               
```

Now you can checkout the commit:
`git checkout a82f0c9`

Now create a new branch
`git switch -c feature`, the command replace the detached Head branch on feature branch






