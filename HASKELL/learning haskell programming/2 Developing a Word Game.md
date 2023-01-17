[[_ 0 Learining Haskell Programming]]

----
[[#Creating a Project with Stack]]
[[#Setting up the Word Game Grid]]
[[#Searching for words]]
[[#Searching in All Directions]]
[[#Unit Testing the Grid with HSpec]]





----

# Creating a Project with Stack

`stack new projectName`
that command create a project folder and gives you some info:
*You can provide them in Stack's global YAML configuration file (`C:\sr\config.yaml`) like this:
      templates:
        params:
          author-email: value
          author-name: value
          category: value
          copyright: value
          github-username: value
      Or you can pass each one on the command line as parameters like this:
      stack new wordgame new-template -p "author-email:value" -p "author-name:value" -p "category:value" -p
      "copyright:value" -p "github-username:value"* 

`vim C:\sf\config.yaml`

again : `stack new wordgame`
in that new folder: `stack ghci` to **compile** the code
look at
- `app/Main.hs` 
- `src/Lib.hs`
- `test/Spec.hs`

`projectName.cabal` has all info to build the project

**build** project
`stack build` (it creates `Linking .stack-work\dist\8a54c84f\build\wordgame-exe\wordgame-exe.exe ...` )
->
`> stack exec wordgame-exe.exe`
`someFunc`







----
# Setting up the Word Game Grid













-----
# Searching for words


















--------
# Searching in All Directions














----
# Unit Testing the Grid with HSpec



















