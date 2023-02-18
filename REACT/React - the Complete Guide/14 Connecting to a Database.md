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

other syntax
**before**
```js
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
```







