#react/database 

==If you connect a React app with Database, database credentials would be exposed in the browser!!!==
You have to connect your app to a backend app (NodeJs, PHP, ...), and this app will be connected to the database.

# API
#api
It is something that has clearly defined interface.
*different urls                 ->    different data*
*different entrypoint   ->    different results*


# Sending a GET request

`axios` makes sending HTTP requests and dealing with responses very simple

## built-in  mechansim for sending HTTP requests
## `fetch api`
It is built in the browser and it allows us to **fetch** data and **send** data.

`fetch('https://swapi.dev/api/films/', {});` this code sends a HTTP request ( `{}` the second argument is a JS object with some additianl options - e.g. with `method` but be default it is a `GET` method)

#promise
`fetch()` returns **a promise** which allows us to then react to the response or any potential errors we moght be getting

>[!important] promise
>it is an object which will eventuall yield some data instead of immediately doing that  because sending an HTTP request  is an asynchron

