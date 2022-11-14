[[_ intro Python Docker]]
[[6 - Creating Container Images]]

---

[[6 Docker Build Command]]
[[6 Base Image - FROM and ARG instructions]]


---

# COPY instruction
`COPY source destination`
`COPY src1 ... srcN Destination/`

- `source` and `destination` use Linux path format (forward slashes `/`)
- `source` and `destination` can be asbolute (starts with `/`) or relative to working directory
- Build Context is both root folder and current working folder for `source`
- If `source` is a folder, its __content__ is copied recursively to `destination` direcotry

## COPY files & directories
```
COPY src_file dst_file
COPY src_file dst_dir/
COPY src_dir dst_dir/
COPY dir_namedst/dir_name/
COPY *.py dst_dir/*
```

## COPY and file ownershipt
>`docker build` executes all instructions as a root user (a Linux superuser ) -> this also applies to container dirs/files (so the file owner in the container will be 0 user (root) )

We can change that:
`COPY --chown==user[:group] src dst`
`user` must exist in Image's `/etc/passwd`
`group` must exist in Image's /etc/group



