https://www.haskell.org/ghcup/steps/

[[0 - Haskell intro]]

---------
OK! /home/jarek/.bashrc has been modified. Restart your terminal for the changes to take effect,
or type "source /home/jarek/.ghcup/env" to apply them in your current terminal session.

===============================================================================

All done!

To start a simple repl, run:
  ghci

To start a new haskell project in the current directory, run:
  cabal init --interactive

To install other GHC versions and tools, run:
  ghcup tui

If you are new to Haskell, check out https://www.haskell.org/ghcup/steps/




----------

# Haskell Platform: haskell + batteries
install:
`apt-get install haskell-platform -y`

check:
`haskell-compiler --version`

start:
`ghci`

script:
`file: example.hs`

compile your Program:
`ghc -o example example.hs`

run:
`./example`

remove haskell platform:
`apt-get remove haskell-platform -y`

---
# Docker Haskell
#docker 

`docker pull haskell`
`docker run -it --rm haskell`


`docker run -it -v ${PWD}:/app --name goodhaskell haskell:9 bash`

