#docker #django  #docker-compose 

struktura projektu
folder_główny:
	- folder z projektem Django
	- plik `docker-compose.yml`
	- `Dockerfile`
	- `requirements.txt`

Dockerfile
```Dockerfile
FROM python:3.9

# katalog pracy wewnątrz kontenera
WORKDIR /app

COPY requirements.txt /app/

RUN pip install --no-cache-dir -r requirements.txt

# kopiowanie aplikacji do kontenera
COPY . /app/

ENV DJANGO_ENV=development

CMD ["python3", "manage.py", "runserver", "0.0.0.0:8000"]

```

docker-compose.yml
```yml
version: "3"

services:
  web:
    build: .
    ports:
      - "8000:8000"
    volumes:
      - ./my_proj_mosh/:/app
    environment:
      - DJANGO_ENV=development
```

requirements.txt
```txt
Django>=3.2,<4

```


## Dockerfile
określa jak zbudować nasz obraz Docker dla aplikacji 


`FROM python:3.9` określenie obrazu bazowego, na którym będziemy budować nasz obraz Dockera

`WORKDIR /app` ustawienie pracy wewnątrz kontenera, wszystkie późniejsze instrukcje będą działać w kontekście tego katalogu

`COPY requirements.txt /app/` kopiuje `requirements.txt` z katalogu, w którym znajduje się plik `Dockerfile` do katalogu `/app/` wewnątrz kontenera

`RUN pip install --no-cache-dir -r requirements.txt` instalowanie zależności przez wykonanie instrukcji `pip`

`ENV DJANGO_ENV=development` ustawia zmienną środowiskową 


-----
## docker-compose.yml

`services` definiuje usługi (kontenery) w naszym projekcie 

`web` nazwa usługi(kontenera), można użyć dowolnej nazwy, ale wartością domyślną jest `web` (w kontenerach webowych)

`build:. ` obraz dla tej usługi będzie budowany z katalogu bieżącego (to katalog,w którym znajduje się `docker-compose.yml`) za pomocą pliku `DOckerfile` -- to odpowiednik komendy `docker build` , ale wykonuje ją w kontekście tej usłudi

`ports: ` mapuje porty między kontenerem a hostem *HOST:CONTAINTER*

`volumes` montuje katalog z lokalnego systemy do katalogu wewnątrz kontenera (montujemy katalog `my_proj_mosh` z lokalnego systemu do katalogu `/app` wewnatrz kontenera ) ( łatwe odzwierciedlanie zmian wewnątrz kontenera)

`envirement`  definiuje zmienne środowiskowe wewnątrz kontenera












