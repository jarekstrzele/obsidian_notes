#mongodb  #youtube #bro_code 

https://www.youtube.com/watch?v=c2M-rlkkT5o

--------
# Intro

- a document is like a single row  in SQL
-  data are store in a document as *key-value* pair (`BSON`)
- a principle: *data which is frequently accessed together is stored together*  

## document
It is a group of field `key-value` pairs to represent an object
```JSON
{
	"name": "Sponge",
	"age": 22
}
```

## collection
It is a group of one or more document
e.g. *students*, *teachers*, *courses*

## database
It is a group of one or more documents

# Installation

https://www.mongodb.com/docs/manual/installation/

`http mongodb> resource > server > installation` choose *Community Edition*
and install `mongosh` - mongodb shell

------------
## docker
- Obraz `mongo` to oficjalny obraz Docker zawierający serwer MongoDB. Pozwala na uruchomienie instancji bazy danych MongoDB w kontenerze.
`docker run -d -p 27017:27017 --name moja-baza-danych mongo`

- Obraz `mongo-express` to narzędzie do zarządzania bazą danych MongoDB za pomocą interfejsu graficznego. Pozwala na przeglądanie, dodawanie, usuwanie i edytowanie danych w bazie MongoDB za pomocą przeglądarki internetowej.
`docker run -d -p 8081:8081 --link moja-baza-danych:mongo mongo-express`
> wyjaśnienie: `moja-baza-danych:mongo`
> wewnątrz kontenera `mongo-express`  kontener `moja-baza-danych` będzie dostępny za pomocą aliasu `mongo`
> 

> - obraz `mongo` dostarcza silnik bazy danych MongoDB, natomiast 
> - obraz `mongo-express` dostarcza interfejs użytkownika do zarządzania bazą danych MongoDB, wykorzystując dostęp do serwera MongoDB. 
> - 
> Oba obrazy mogą współpracować, co pozwala na skorzystanie z interfejsu graficznego do zarządzania bazą danych MongoDB uruchomioną w kontenerze `mongo`.

-------------













