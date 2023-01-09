[[7 - Intro Docker Compose]]


[[7 Example 2 Microservice & SQL Database]]
[[7 Example 3 Django Web Site]]

---
# TensorFlow & TensorBoard
![[docker-tensorFlow_TensorBoard.excalidraw | 700]]

`d4py/section-7/ml-model`


```yml
version: "3.7" # Mandatory line in docker compose file

services: # declaration of containers (here named services) to run
  tf: # jupiter+TenserFlow Container
    image: tensorflow/tensorflow:latest-py3-jupyter
    ports:
      - "8888:8888" #declare Port mapping as a string due to yaml processin of xx:xx
    volumes:
      - ./notebooks:/tf/notebooks
      - ./logs:/tf/logs

  tb: 3 tensorboard container
    image: tensorflow/tensorflow
    command: tensorboard --bind_all --logdir /tf/logs # Override CMD from Image Metadata
    ports:
      -"6006:6006"
    volumes:
      -./logs:/tf/logs
      
```

---
1. `docker-compose pull` ![[7 Docker Compose command reference#images]]
2. `docker-compose up` ![[7 Docker Compose command reference#bring up]]
3. to stop `ctrl+C` (`docker-compose ps`, `docker-compose down`)








