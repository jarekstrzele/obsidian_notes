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
>it is an object which will eventuall yield some data instead of immediately doing that  because sending an HTTP request  is an asynchronous task it doesn't finish immediately
>so we can't execuse the next line of code, because we haven't yet got data

`fetch().then().catch()`  the final function will be calle whenever we got a response and you can add `catch` to handle any potential errors

to transform JSON  data to a real JS object   use `.json()` method

```jsx
  function App() {
  const[movies, setMovies] = useState([])
  function transformedMovies(){
    fetch('https://swapi.dev/api/films/')
    .then( response => {
        return response.json();
      }).then(data => {
        const transformedMovies = data.results.map(movieData => {
          return {
            id: movieData.episode_id,
            title: movieData.title,
            openingText: movieData.opening_crawl,
            releaseDate: movieData.release_date
          }
        })
        setMovies(transformedMovies);
      });
  }

  return (
    <React.Fragment>
      <section>
        <button onClick={transformedMovies}>Fetch Movies</button>
      </section>
      <section>
        <MoviesList movies={movies} />
      </section>
    </React.Fragment>
  );
}
```

### other syntax to async executing
**before**
```js
function transformedMovies(){
    fetch('https://swapi.dev/api/films/')
    .then( response => {
        return response.json();
      }).then(data => {
        const transformedMovies = data.results.map(movieData => {
          return {
 ...
```

**after**
```js
  async function transformedMovies(){
    const response = await fetch('https://swapi.dev/api/films/') ;
    const data = await response.json() ;
    const transformedMovies = data.results.map( movieData => {
          return {
...
```


#  FeedBack
```jsx
import React, { useState } from 'react';
import MoviesList from './components/MoviesList';
import './App.css';

function App() {
  const[movies, setMovies] = useState([])
  const[isLoading, setIsLoading] = useState(false)
  ...
        

  return (
    <React.Fragment>
      <section>
        <button onClick={transformedMovies}>Fetch Movies</button>
      </section>
      <section>
        { !isLoading && movies.length > 0 && <MoviesList movies={movies} />}
        { !isLoading && movies.length === 0 && <p> Found no movies. </p> }
        {isLoading && <p>Loading ...</p>}
      </section>
    </React.Fragment>
  );
}

export default App;
```

----
# ErrorHandler
`fetch` doesn't support real errors
`axios` support errors

but in `fetch` a response object has `ok` field or `status` field which holds the concrete response status code.

```js
function App() {
  const[movies, setMovies] = useState([])
  const[isLoading, setIsLoading] = useState(false)
  const[error, setError] = useState(null);

  async function transformedMovies(){
    setIsLoading(true) ;
    setError(null);
    try{
      const response = await fetch('https://swapi.dev/api/film/') ;
      if(!response.ok) {
        throw new Error('SOmthing went wrong')
      }

      const data = await response.json() ;

      const transformedM...

  //..............

    }
  return (
    <React.Fragment>
      <section>
        <button onClick={transformedMovies}>Fetch Movies</button>
      </section>
      <section>
        { !isLoading && movies.length > 0 && <MoviesList movies={movies} />}
        { !isLoading && movies.length === 0 && !error && <p> Found no movies. </p> }
        { !isLoading && error && <p> {error}</p> }
        {isLoading && <p>Loading ...</p>}
        </section>
    </React.Fragment>
  );	  
	  
```



------------
# `useEffect()` for Requests
#useEffect 

TO IMMEDIATELY FETCH DATA -> use `useEffect`
*sending the HTTP request is a side effect which ultimately changes our components state*

if you will have code:
```js
function App() {
  const[movies, setMovies] = useState([])
  const[isLoading, setIsLoading] = useState(false)
  const[error, setError] = useState(null);
  
  useEffect( () => {
    fetchMoviesHandler();
  }) ;
  async function fetchMoviesHandler(){
    setIsLoading(true) ;
    setError(null);
    try{
```

this code is not good because whenever this component will be reevaluate the function from useEffect wil be executed

but you can add the second arg of `useEffect` function which is the array of dependencies, **where we define WHEN this EFECT function should be executed again**; it will be execute, if the depencencies listed here change
```js
  useEffect( () => {
    fetchMoviesHandler();
  }, []) ;
```
because the list is empty, this functio will be executed only on time at the begining


this will be infinit loop
```jsx  useEffect( () => {
    fetchMoviesHandler();
  }, [fetchMoviesHandler]) ;
```

so, you can use `useCallback` 
[[useCallback]] 
`useCallback(<function>, [<exteral depenecies>])`


```jsx
..  
  const fetchMoviesHandler = useCallback( async () =>{
    setIsLoading(true) ;
    setError(null);
    try{
      const response = await fetch('https://swapi.dev/api/films/') ;
      if(!response.ok) {
        throw new Error('SOmthing went wrong')
      }
  
      const data = await response.json() ;

      const transformedMovies = data.results.map( movieData => {
            return {
              id: movieData.episode_id,
              title: movieData.title,
              openingText: movieData.opening_crawl,
              releaseDate: movieData.release_date
            } ;
          }) ;

          setMovies(transformedMovies);
          setIsLoading(false)
        }
      catch(error){
        setError(error.message) ;
        setIsLoading(false) ;
    }

    }, []);

  useEffect( () => {
    fetchMoviesHandler();
  }, [fetchMoviesHandler]) ;

  return (
    <React.Fragment>
      <section>
...
```


-----
# Firebase
#firebase
login by google account
`>` Realtime Database -> it has nice rest api
	> create database > start in Test Mode  -> **it  gives you a URL  which you can talk to that database** this is ==dynamic rest API ==
	
`https://react-http-9f6af-default-rtdb.firebaseio.com/`
dynamicaly -> `https://react-http-9f6af-default-rtdb.firebaseio.com/movies.json`

in App.js there is a component `<AddMovie onAddMovie={addMovieHandle} />`
to convert a JS object to json use `JSON.stringify(jsObject)`
```js
  function addMovieHandler(movie) {
    fetch('https://react-http-9f6af-default-rtdb.firebaseio.com/movies.json', {
      method: 'POST',
      body: JSON.stringyfy(movie),
      headers:{
        'Content-Type': 'application.json'
      }
    });
  }
```

you can use other syntax
```js
  async function addMovieHandler(movie) {
    const response = await fetch('https://react-http-9f6af-default-rtdb.firebaseio.com/movies.json', {
      method: 'POST',
      body: JSON.stringyfy(movie),
      headers:{
        'Content-Type': 'application.json'
      }
    });
    const data = await response.json() ;
    console.log(data) ;
  }
```

```jsx
  const fetchMoviesHandler = useCallback(async () => {
    setIsLoading(true);
    setError(null);
    try {
      const response = await fetch('https://react-http-9f6af-default-rtdb.firebaseio.com/movies.json');
      if (!response.ok) {
        throw new Error('Something went wrong!');
      }

      const data = await response.json();
      const loadedMovies = []

      for (const key in data){
        loadedMovies.push({
          id: key
        , title: data[key].title
        , openingText: data[key].openingText
        , releaseDate: data[key].releaseDate
        })
      }
      // const transformedMovies = data.map((movieData) => {
      //   return {
      //     id: movieData.episode_id,
      //     title: movieData.title,
      //     openingText: movieData.opening_crawl,
      //     releaseDate: movieData.release_date,
      //   };
      // });

      setMovies(loadedMovies);
    } catch (error) {
      setError(error.message);
    }
    setIsLoading(false);
  }, []);

  useEffect(() => {
    fetchMoviesHandler();
  }, [fetchMoviesHandler]);

  async function addMovieHandler(movie) {
    const response = await fetch('https://react-http-9f6af-default-rtdb.firebaseio.com/movies.json', {
      method: 'POST',
      body: JSON.stringify(movie),
      headers:{
        'Content-Type': 'application.json'
      }
    });
    const data = await response.json() ;
    console.log(data) ;
  }

  let content = <p>Found no movies.</p>;
  if (movies.length > 0) {
    content = <MoviesList movies={movies} /> ;
  }
  if (error) {
    content = <p>{error}</p>;
  }
  if (isLoading) {
    content = <p>Loading...</p>;
  }

  return (
    <React.Fragment>
      <section>
        <AddMovie onAddMovie={addMovieHandler} />
      </section>
      <section>
        <button onClick={fetchMoviesHandler}>Fetch Movies</button>
      </section>
      <section>{content}</section>
    </React.Fragment>
  );
}

export default App;
```


























