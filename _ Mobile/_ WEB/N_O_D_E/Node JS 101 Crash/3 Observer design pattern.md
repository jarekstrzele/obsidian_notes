[[_ NodeJS 101 Crash Course]]

- one subject can have many observers
- one subject can emit series of events - e.g.
		- button:
			- hover event
			- click event
		- database and CRUD
		- chat app
- each observer can react on an event in his way

------
# Event emitter
to be get notified of events - *call back functions*

`event` module allows us to have a subject that emits events

`process` is an instance of emitter


```js
const EventEmitter = require('events') ;
const celebrity = new EventEmitter();

// subscribe to celebrity for observer 1
celebrity.on('race win', () => {
	console.log('COngraturlatiions You are the best')
})
// subscribe to celebrity for observer 2
celebrity.on('race win', () => {
	console.log('I could have better than that!!!')
})

process.on('exit', (code) => {
    console.log('Process exit event with code: ', code) ;
})

celebrity.emit('race win') ;
celebrity.emit('race lost') ;
celebrity.emit('race win') ;
```

```bash
$ node eventemit.js
COngraturlatiions You are the best
I could have better than that!!!
COngraturlatiions You are the best
I could have better than that!!!
Process exit event with code:  0
```







