
[[0 - Haskell intro]]


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

