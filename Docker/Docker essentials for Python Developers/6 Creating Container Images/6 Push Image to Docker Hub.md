[[6 - Creating Container Images]]





---
# Push Image to Docker Hub

`docker login`
`docker tag img account/image:tag`
`docker push account/image:tag`

- docker engine must have valid DOcker Hub login credentials -us `docker login`
- image name must include DOcker Hub account name (or namespace)


# push to other image registries
`docker push myregistry.com:5001:cb:prod`





