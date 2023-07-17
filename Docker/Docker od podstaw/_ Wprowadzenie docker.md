#udemy 

----
[[1 Uruchamianie kontenerów]]



----------
# Zmiany 2019-22
- 2019 przejęcie Docker Enterprise przez Mirantis
- 2022 różnice w subskrypcji (docker desctop
- pojawienie się standaryzacji w tworzenie obrazów, silników 

# Wprowadzenie do dockera

>[!info] Docker
>Otwarte oprogramowanie służące jako "platforma dla programistów i administratorów do tworzenia, wdrażania i uruchamiania aplikacji rozproszonych" (wiki)

------
# Wprowadzenie
Kontenery są "lżejsze" od maszyn wirtualnych.

Docker stworzony przez firmę *dotCloud*.
2013 udostępniony publicznie (na githubie)
Obecnie rozwijane i wspierane przez (Google, Microsoft, IBM, Red Hat, Cisco)

**Zalety**
- szybkość:
	- development, 
		- wszystkie zależności spakować w obraz
		- nowy developer uruchamia taki obraz lokalnie na swojej maszynie bez problemu
	- budowanie, 
	- testowanie, 
	- deployment
		- skalowalność
		- reużywalność
		- izolacja
		- łatwość budowy mikro-serwisów (każda usługa w innym kontenerze)
- redukcja złożoności
- izolacja
- 

# Architektura
- zbudowana na architekturze *klient-serwer* - składa się z trzech części:
	- *docker daemon* - część SERWEROWA
		- zarządzanie wszystkimi obiektami (obrazy, kontenery, sieci,dyski)
	- *REST API* służy do komunikacji z częścią serwerową 
	- *docker CLI* - KLIENT (różne polecenia z linii komend, aby komunikować się z serwerem):
		- nie musi być uruchomiony na tej samej maszynie co serwerowa część
		- nie musi być w formie terminalowej, może mieć wersję graficzną


![[docker_architecture.excalidraw|700]]

https://hub.docker.com


----
# Koncepty Dockera

### *images*
jest jak klasa
tworzony w pliku `Dockerfile`
```dockerfile
FROM nginx:latest

WORKDIR /usr/share/nginx/html

COPY index.html index.html
```


### *containers*
jest jak obiekt


-----
# instalacja

## Linux
####  instalacja dockera
https://docs.docker.com/engine/install/ubuntu/

aby uruchamiać dockera bez `sudo`
## `sudo usermod -aG docker $USER`

```bash
$ sudo usermod -aG docker $USER
jarek@jarek-legion:~$ echo $USER
jarek

```


#### instalacja `docker Compose`
https://docs.docker.com/compose/install/linux/




