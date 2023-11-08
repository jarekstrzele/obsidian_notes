[[_ Intro Linux Shell]]

---

# Permissions
```bash
$ ls -l
-rwxr-xr-x  ...
....
drwxr-xr-x ...

```
1. file, owner (read,write,execute), group (read, execute), all( read, execute)
first
- `-` a file
- `d` a directory
- `l` symbolik link 

Next three groups list the permissions for:
- owner
- owners group
- all users
`r` read permission
`w` write permission
`x` execute permission
`A` denies a permission

### Changing File Permissions
4 for read
2 for write
1 for execute

`rwx` is $4+2+1=7$ 
`rw-` is 4+2 = 6
`r-x` is $4+1=5$

`rw-rw-r--` has a binary permission of $664$

`chmod <new permissions> filename`
`chmod 644 test` 

