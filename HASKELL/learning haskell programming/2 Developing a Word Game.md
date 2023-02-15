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

### create
again : `stack new wordgame`

### compilend build
in that new folder: `stack ghci` to **compile** the code
look at
- `app/Main.hs` 
- `src/Lib.hs`
- `test/Spec.hs`

or build by
**build** project
`stack build` (it creates `Linking .stack-work\dist\8a54c84f\build\wordgame-exe\wordgame-exe.exe ...` )


### cabal file - metadata
`projectName.cabal` has all info to build the project
you can change metadata in `projectName.cabal` (e.g. add to `ghc-option`  `-dynamic`)

### run
`> stack exec wordgame-exe`
`someFunc`
```bash
$ .stack-work/dist/x86_64-linux/Cabal-3.6.3.0/build/wordgame2-exe/wordgame2-exe
someFunc!!!!
jarek@pop-os:~/Desktop/haskell_simple_console/wordgame2$ stack exec wordgame2-exe
someFunc!!!!
```



### test
`stack test`
by default is not implemented
you can add som code to `test/Spec.hs`
first-maybe-`stack install hspec`
add to the file 
```haskell
import Test.Hspec
main :: IO ()
main = hspec $ do
    describe "How to write a test" $ do
        it "Should be able to run test" $ do
            someFunc `shouldBe` "someFunc"
```


but you have to add to `.cabal` to `build-depends:`  `hspec`
```haskell
test-suite wordgame-test
  type: exitcode-stdio-1.0
  main-is: Spec.hs
  other-modules:
      Paths_wordgame
  hs-source-dirs:
      test
  ghc-options: -Wall -Wcompat -Widentities -Wincomplete-record-updates -Wincomplete-uni-patterns -Wmissing-export-lists -Wmissing-home-modules -Wpartial-fields -Wredundant-constraints -threaded -rtsopts -with-rtsopts=-N
  build-depends:
      base >=4.7 && <5
    , wordgame
    , hspec
  default-language: Haskell2010
```


----
# Setting up the Word Game Grid













-----
# Searching for words


















--------
# Searching in All Directions














----
# Unit Testing the Grid with HSpec



















