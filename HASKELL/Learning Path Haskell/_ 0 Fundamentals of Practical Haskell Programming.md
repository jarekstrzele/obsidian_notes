#udemy #haskell  #cook_richard

[[1 Exploring Haskell]]
[[2 Haskell in Depth]]

----
# Stack

https://docs.haskellstack.org/en/stable/

>[!info] The Haskell Tool Stack
>It is a cross-platform program for developing Haskell projects

install

verify 
```powershell
C:\Users\jaros>where stack
C:\ghcup\bin\stack.exe
```

create a stack project
```powershell
PS C:\Users\jaros\Desktop\Prog> stack new first-stack-project
Downloading template "new-template" to create project "first-stack-project" in first-stack-project\ ...


```

- it creates a new directory that contains all the files needed to start a project correctly, using a default template
- go to that folder
- `stack build` - will build the template project and create an executable named `first-stack-project-exe.exe`
- `stack exec first-stack-project-exe` will run (execute) the built executable










