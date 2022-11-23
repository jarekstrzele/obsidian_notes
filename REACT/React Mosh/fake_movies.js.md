[[fake_genders.js]]
[[3.1 Component vidly project]]

```js
import * as genresAPI from "./fake_genders.js";

  

const movies = [

{

_id: "15",

title: "Terminator",

genre: { _id: "1818", name: "Action" },

numberInStock: 6,

dailyRentalRate: 2.5,

publishDate: "2018-01-03T19:04:28.809Z"

},

{

_id: "16",

title: "Die Hard",

genre: { _id: "1818", name: "Action" },

numberInStock: 5,

dailyRentalRate: 2.5

},

{

_id: "17",

title: "Get Out",

genre: { _id: "1820", name: "Thriller" },

numberInStock: 8,

dailyRentalRate: 3.5

},

{

_id: "19",

title: "Trip to Italy",

genre: { _id: "1814", name: "Comedy" },

numberInStock: 7,

dailyRentalRate: 3.5

},

{

_id: "1a",

title: "Airplane",

genre: { _id: "1814", name: "Comedy" },

numberInStock: 7,

dailyRentalRate: 3.5

},

{

_id: "1b",

title: "Wedding Crashers",

genre: { _id: "1814", name: "Comedy" },

numberInStock: 7,

dailyRentalRate: 3.5

},

{

_id: "1e",

title: "Gone Girl",

genre: { _id: "1820", name: "Thriller" },

numberInStock: 7,

dailyRentalRate: 4.5

},

{

_id: "1f",

title: "The Sixth Sense",

genre: { _id: "1820", name: "Thriller" },

numberInStock: 4,

dailyRentalRate: 3.5

},

{

_id: "21",

title: "The Avengers",

genre: { _id: "1818", name: "Action" },

numberInStock: 7,

dailyRentalRate: 3.5

}

];

  

export function getMovies() {

return movies;

}

  

export function getMovie(id) {

return movies.find(m => m._id === id);

}

  

export function saveMovie(movie) {

let movieInDb = movies.find(m => m._id === movie._id) || {};

movieInDb.name = movie.name;

movieInDb.genre = genresAPI.genres.find(g => g._id === movie.genreId);

movieInDb.numberInStock = movie.numberInStock;

movieInDb.dailyRentalRate = movie.dailyRentalRate;

  

if (!movieInDb._id) {

movieInDb._id = Date.now();

movies.push(movieInDb);

}

  

return movieInDb;

}

  

export function deleteMovie(id) {

let movieInDb = movies.find(m => m._id === id);

movies.splice(movies.indexOf(movieInDb), 1);

return movieInDb;

}
```