#python #firebase #hala #youtube 
https://www.youtube.com/watch?v=s-Ga8c3toVY

you have to add  a desktop app to firebase as a web app (look at Project overview of your FireBase Project (e.g. test))

after registration:
```javascript
// Import the functions you need from the SDKs you need
import { initializeApp } from "firebase/app";
// TODO: Add SDKs for Firebase products that you want to use
// https://firebase.google.com/docs/web/setup#available-libraries

// Your web app's Firebase configuration
const firebaseConfig = {
  apiKey: "AIzaSyBSpLK0ThyXOuOXMgl_oYF0iQ8I7Qlh6oc",
  authDomain: "test-7a2ea.firebaseapp.com",
  databaseURL: "https://test-7a2ea-default-rtdb.firebaseio.com",
  projectId: "test-7a2ea",
  storageBucket: "test-7a2ea.appspot.com",
  messagingSenderId: "455697270541",
  appId: "1:455697270541:web:c625f5c109b77c811b1244"
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);
```

copy `const firebaseConfig` to your python file and keys change to string
```python
firebaseConfig = {
  "apiKey": "AIzaSyBSpLK0ThyXOuOXMgl_oYF0iQ8I7Qlh6oc",
  "authDomain": "test-7a2ea.firebaseapp.com",
  "databaseURL": "https://test-7a2ea-default-rtdb.firebaseio.com",
  "projectId": "test-7a2ea",
  "storageBucket": "test-7a2ea.appspot.com",
  "messagingSenderId": "455697270541",
  "appId": "1:455697270541:web:c625f5c109b77c811b1244"
};

firebase=pyrebase.initialize_app(firebaseConfig)
```








