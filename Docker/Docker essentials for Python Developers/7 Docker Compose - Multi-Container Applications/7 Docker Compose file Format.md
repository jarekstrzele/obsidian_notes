[[7 - Intro Docker Compose]]


[[7 Key COncepts of Docker Compose]]



---
# Docker Compose file Format
It uses `yaml` syntax (key:value).
>         **YAML Indentention!!!**

```yml
version: "3.7"
# Comments
volumes:
...
networks:
...
services:
...

```


## Services
`services` is a list of service declaration
```yml
services:
  service_name:
    image: myimage:1.0
    ports:
      - "5000:5000"
      - "8001: 8000"
    volumes:
      - db_vol:/data
    networks:
      - backend
    environment:
      - VAR=value
```

services: image, ports, volumes, networks, environment


## Volume & Network Declarations
```yml
volumes:
  db_vol:
  files_vol:

networks:
  frontend:
  backend:
```



