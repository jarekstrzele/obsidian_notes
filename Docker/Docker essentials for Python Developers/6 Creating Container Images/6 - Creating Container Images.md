[[_ intro Python Docker]]

[[4 - Docker containers Basics]]
[[5 - Running Docker Containers]]

---
# Creating Container Images
[[6 Docker Build Command]]
[[6 Base Image - FROM and ARG instructions]]

[[6 COPY instruction]]
[[6 RUN instruction]]
[[6 VOLUME instruction]]
[[6 Start-up Command ENTRYPOINT & CMD]]
[[6 Push Image to Docker Hub]]

---
## Overview of Image Build Process

an __IMAGE__ has to basic components:
- metadata
	- "Os": "Linux"
	- "Architecture": "amd64"
	- ...
- filesystem:
	- flask
	- python
	- debian


## Image Build Process
- start with base image
- copy source code, configuration & data files
- install required system Packages & Python Libraries
- Modify Metadata:
	- working directory
	- volume mount points & exposed ports
	- environment variables
	- labels
	- start-up command
- commit the image, add Name & tag

### two ways of building image
#### manual process
1. Base Image
2. copy data config, cource
3. omsta;; sw
4. commit & set metadata
FINAL IMAGE
[[6 manual build process]]


#### automated process
1. Dockerfile (it is a script)
2. `docker build ...`
FINAL IMAGE
[[6 automated build process]]








