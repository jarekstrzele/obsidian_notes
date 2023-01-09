[[fake_movies.js]]

```js

export const genres = [

{ _id: "1818", name: "Action" },

{ _id: "1814", name: "Comedy" },

{ _id: "1820", name: "Thriller" }

];

export function getGenres() {

return genres.filter(g => g);

}
```