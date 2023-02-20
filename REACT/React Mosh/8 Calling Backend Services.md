#react @axios

Fake online REST API for Testing and PROTOTYPING
REST - representatial state transfer 

http://jsonplaceholder.typicode.com/ - it provides a bunch of endpoints that are publicly accessible over the internet
- you can send http requests to these endpoint to CRUD
- you refer to these endpoints as API's
- http://jsonplaceholder.typicode.com/posts `posts` it it a endpoint
	- sending http requests to this endpoint you cand make CRUD

**IN REACT YOU HAVE TO SEND HTTP REQUESTS TO CRUD**
How to send them>
- use `Fetch API`
- use `jQuery AJAX`
- use `Axios` the word from greek (worthy or suitable)
-----------
[[#`GET`]]
[[#`POST`]]











--------------
# AXIOS
``npm i axios``

## `GET`

### `axios.get('http://jsonplaceholder.typicode.com/posts')` - it returns a promise 

>[!info] a promise
>- It is an object that holds the result of an asynchronous operation
>- an asynchronous operation is an operation that is going to complete in the future

```js
  componentDidMount(){
    //pending > resolved (success) or rejected (failure)
    const promise = axios.get('http://jsonplaceholder.typicode.com/posts') ;
    // console.log(promise) ; // internal attrs: promisestatus, promisevalue/promiseresult
    // promise.then() -> you can replace await promise
    // const response = await promise;
  }
```

but when you use `await` you have to decorate the function `async`
```js
  async componentDidMount(){
    //pending > resolved (success) or rejected (failure)
    const promise = axios.get('http://jsonplaceholder.typicode.com/posts') ;
    // console.log(promise) ; // internal attrs: promisestatus, promisevalue/promiseresult
    // promise.then() -> you can replace await promise
    const response = await promise;
    console.log(response) ;
  }
```

and better way
```js
async componentDidMount(){
    //pending > resolved (success) or rejected (failure)
    const response = await axios.get('http://jsonplaceholder.typicode.com/posts') ;
    console.log(response) ;
  }
```


Appjs.
```jsx
class App extends Component {
  state = {
    posts: []
  };

  async componentDidMount(){
    //pending > resolved (success) or rejected (failure)
    const {data: posts } = await axios.get('http://jsonplaceholder.typicode.com/posts') ;
    this.setState({ posts }) ;
  }

  handleAdd = () => {
    console.log("Add");
  };

  handleUpdate = post => {
    console.log("Update", post);
  };

  handleDelete = post => {
    console.log("Delete", post);
  };

  render() {
    return (
      <React.Fragment>
        <button className="btn btn-primary" onClick={this.handleAdd}>
          Add
        </button>
        <table className="table">
          <thead>
            <tr>
              <th>Title</th>
              <th>Update</th>
              <th>Delete</th>
            </tr>
          </thead>
          <tbody>
            {this.state.posts.map(post => (
              <tr key={post.id}>
                <td>{post.title}</td>
                <td>
                  <button
                    className="btn btn-info btn-sm"
                    onClick={() => this.handleUpdate(post)}
                  >
                    Update
                  </button>
                </td>
                <td>
                  <button
                    className="btn btn-danger btn-sm"
                    onClick={() => this.handleDelete(post)}
                  >
                    Delete
                  </button>
                </td>
              </tr>
            ))}
          </tbody>
        </table>
      </React.Fragment>
    );
  }
}

export default App;
```



App.css
```js
.App {
  text-align: center;
}

.App-logo {
  animation: App-logo-spin infinite 20s linear;
  height: 80px;
}

.App-header {
  background-color: #222;
  height: 150px;
  padding: 20px;
  color: white;
}

.App-title {
  font-size: 1.5em;
}

.App-intro {
  font-size: large;
}

@keyframes App-logo-spin {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}
```


------------

## POST
App.js
```js
const apiEndPoint = "http://jsonplaceholder.typicode.com/posts" ;

class App extends Component {
  state = {
    posts: []
  };

  async componentDidMount(){
    //pending > resolved (success) or rejected (failure)
    const {data: posts } = await axios.get(apiEndPoint) ;
    this.setState({ posts }) ;
    // console.log(this.state.posts) ;
  }

  handleAdd = async () => {
   const obj = { title: 'a', body:'b'} ;
   const {data: post } = await axios.post(apiEndPoint, obj) ;
   console.log(post) ;
   const posts = [post, ...this.state.posts];
   this.setState({posts})
  };

  handleUpdate = post => {
    console.log("Update", post);
  };

  handleDelete = post => {
    console.log("Delete", post);
  };
```




















