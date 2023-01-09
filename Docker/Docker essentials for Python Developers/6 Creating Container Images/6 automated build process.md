[[_ intro Python Docker]]

[[6 - Creating Container Images]]
[[6 manual build process]]

---
# Automated build process
This process is performed by `docker build ...` command and a special script called `Dockerfile` (describ all steps to create a docker image ; it is an imperative script)

```Dockerfile
# comment
FROM base-image
INSTRUCTION args
INSTRUCTION args \
args ...
INSTRUCTION args # comment

```



## Filesystem modification instructions
- declare base image:
`FROM base-image`
- copy files and directories from build context to image filesystem:
`COPY from to`
- Execute a command during build time (non-interactive commands only)
`RUN command-line`


## Metadata Modification Instructions
- set/create working directory:
`WORKDIR /directory/subdirectory`
- define environment variable:
`ENV variable value`
- declare mount point:
`VOLUME /mount/point`
- declare exposed port:
`expose port`
- define start -up command:
`ENTRYPOINT ["/bin/binary", "/opt"]`
`CMD ["opt", "arg"]`
















