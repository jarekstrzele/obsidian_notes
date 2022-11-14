[[_ intro Python Docker]]
[[5 - Running Docker Containers]]


---

# Pull the Image

`docker image pull <image>`
`docker pull <image>`

- skip Image Tag to pull `:latest`
image is downloaded only if registry has newer version
use `-a` or `--all-tags` to download all Tags of the Image 
- consider disk space and time required!

---

# Rename Image
`docker image tag <image> <new_name>`
`docker tag <image> <new_name>`

- adds `<new_name>` to existing Image
- One image may have multiple names
- remove image name with `docker rmi`

We rename images because:
- we want to short a long name
- we want to upload an image to not standard registry and add a new name

```bash
$ docker pull gcr.io/google-containers/python:3.5.1-slim

$ docker tag gcr.io/google-containers/python:3.5.1-slim python:gcr
```

---

# List and delete images
`docker image ls [<image>]`
`docker images [<image>]`
`docker image rm <image>`
`docker rmi <image>`
`docker image prune [-a] [-f]` remove unnamed images


- image List Command displays all images in local image cach, if no args are used
- Use `-f` option to force remove an Image
- 

> one image -> many names
> one name -> one image

`docker images -a` shows all images (even without names)

`docker prune` deletes all unused and unnamed images
```bash
$ docker image prune
WARNING! This will remove all dangling images.
Are you sure you want to continue? [y/N] y
```

---
# Inspect Image Metadata

`docker image inspect <image>`  or
`docker inspect <image>` to get detailed metadata information for the image

`docker history <image>` or
`docker image history <image>` to see how the image has got built
































