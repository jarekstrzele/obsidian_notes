#udemy #haskell  #cook_richard

[[1 Exploring Haskell]]
[[2 Haskell in Depth]]

----
# Stack

https://docs.haskellstack.org/en/stable/

>[!info] The Haskell Tool Stack
>It is a cross-platform program for developing Haskell projects

# install on Windows

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


--------------
# Install on Linux



----

# Fundamentals of Practical Haskell Programming

### FP - Functional Programming
### PL - Programming Language


## FP Way
- it is an alternative model of computation
- treats computation as the evaluation of mathematical functions
- is declarative, emphasizing the "what" over the "how"

### FP programs:
- contain expressions and declarations
- avoid chaging globale state
- avoid mutating data
- avoid looping and, instead, employ recursin or higher-order abstractions

**traversal** (a.k.a. `mapping`) the process of iterating over elements and performing an action on each item
```haskell
main = print $ map (+ 10) [1,2,3]
```

**reduction**(a.k.a. `floding`)the process of iterating over a collection of elements in order to produce some kind of summaryy such as a total
```haskell
main = print $ foldr (+) 0 [1,2,3]
```

**filtering** iterate over a collection of elements and extract the subser for which some predicate holds true
```haskell

```

**compostion** join two or more function together to produce a bigger function
```haskell

```





























