[[_ Intro Scalable Web Applications with Python, Flask and SQLAlchemy]]

[[PostgreSQL]]


---


# Section 6 Git

#git/config #git 
[[_ Preface Git - Practical Guide]]

`git config --global user.name  `
`git config --global user.email  `

git init  
git status  
git add fileName.__  
git commit -m "added some files"  

**GITHUB**  
#github 
-   make a repository  
-   copy a link to this repository (is named origin)  
-   in the terminal:  
```bash
git remote add origin "https://github.com/jarekStrzelecki/flask_basics.git"

# we made a link between local repository and the remote repository  

git push -u origin master  
# origin - default online repo
# master - default branch
# -u next time you will write only 'git push'


(main-master)  

authorisation problems:  
```

account->settings-->Developer settings-->Personal Access tokens:  

Tokens you have generated that can be used to access the GitHub API.  

25 listopada 2021 token: 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  

na koncie js100code, jarekStrzelecki, Filozofia2!@  

`git remote set-url origin https://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@github.com/jarekStrzelecki/flask_basics.git  `

`.git/config`  -- tu są różne informacje  
 
`git remote add origin https://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@github.com/jarekStrzelecki/flask_basics.git -- dodaje remote repository do lokalnego  `

git push -u origin main  
  

## Deleteing file from local and remot repository  
#git/deleting 

`git rm "filename.___"  `
`git commit -m "messega"  `

  
**Deleteing** file only from remote repo:  
`git rm --cached fileName.___ `
(this file remains in the local repo)  
`git commit -m "deleted from remote repo"  `
`git push  `







