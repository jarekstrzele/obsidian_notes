[[7 - Intro Docker Compose]]


---
# Docker Compose command reference

---
*bring up to date* aktualizować
*bring up*  wychowywać
*bring up single service* przywołać pojedynczy serwis
*foreground* pierwszo planowy, *background* tło)

---
## bring up
- Bring up full deployment declared in *docker-compose.yml* in foreground mode: 
>		`docker-compose up`

- bring up full deployment declared in *docker- compose.yml* in background mode
>		`docker-compose up -d`


- bring up single service declared in *docker-compose.yml* in foreground mode
>		`docker-compose up service_name`
>		
>or  in background mode:
>		`docker-compose up -d service_name`

automatically creates Volumes & Networks

## remove
`docker-compose down` remove full deployment declared in *docker-compose.yml* leaving Volumes

`docker-compose down -v` remove full deployment declared in *docker-compose.yml* including Volumes


## rename
`docker-compose -f filename.yml up` use docker compose file with non-standar filename

## validate and check
`docker-compose config`
`docker-compose -f file.yml config`


## logs
`docker-compose logs` print logs of all services declared in*docker-compose.yml*

`docker-compose logs service_name`

Use `...logs -f...` to print logs in real-time, `Control-C` to stop

## images
`docker-compose pull` pull images of services declared in *docker-compose.yml*

`docker-compose build` build images declared in *docker-compose.yml* with `build` attribute


## list
`docker-compose ps [-a]` list containers in deployment declared in *docker-compose.yml*

## run instance
`docker-compose run service command` run ad hoc instance of a Service declared in *docker-compose.yml* in foreground mode:

use `... run --rm service ...` to auto remove the COntainer
use `... run -d service ..` for background mode


























