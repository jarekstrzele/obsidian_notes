[[#Clock in React Native]]


# Clock in terminal -  Node
a test file `clockInTerminal.jsx`
```js
function time_info(){
const now = new Date() ;
console.log(now) ;
const hours = now.getHours() ;
const minutes = now.getMinutes();
const seconds = now.getSeconds();

const year = now.getFullYear() ;
const month_day = now.getDate() // a day of a month (1-31)
const week_day = now.getDay() // 0 -Sunday, 6

const human_date = now.toDateString();
const more_human_date = now.toString();

const options = {weekday: 'long', year: 'numeric', month: 'long'}
const formattedDate = now.toLocaleString('pl-PL', options)

console.log(hours, minutes, seconds) ;
console.log(year, month_day, week_day) ;
console.log(human_date) ;
console.log(more_human_date) ;
console.log("***************") ;
console.log(formattedDate)

}

// https://www.iana.org/time-zones

// https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleString

time_info() ;

const date = new Date();
const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric', hour: 'numeric', minute: 'numeric', second: 'numeric', hour12: false, timeZone: 'Europe/Warsaw' };
const formattedDate = date.toLocaleString('pl-PL', options);
console.log(formattedDate); // wyświetli np. "poniedziałek, 28 marca 2023, 19:20:30"


const print_time = () => {
	const now = new Date() ;
	const hours = now.getHours() ;
	const minutes = now.getMinutes();
	const seconds = now.getSeconds();

	console.log(`${hours}:${minutes}:${seconds}`);
	setTimeout( () => {
		console.clear() ;
	}, 1000) ;
}

print_time() ;
setInterval(print_time, 1000)

function displayTime(){
	const now = new Date() ;
	const timeString = now.toLocaleTimeString();
	process.stdout.write(`\r${timeString}`) ;
}

setInterval(displayTime, 1000);
```

----
# Clock in React Native

`npx create-react-app`

```jsx
import React, { useState, useEffect } from 'react';

import { StyleSheet, Text, View } from 'react-native';

  

export default function App() {

const [time, setTime] = useState(new Date().toLocaleTimeString());

  

useEffect(() => {
   const intervalId = setInterval(() => {
     setTime(new Date().toLocaleTimeString());

}, 1000);

return () => clearInterval(intervalId);

}, []);
 

return (
 <View style={styles.container}>

<Text style={styles.clock}>{time}</Text>

</View>

);
}

const styles = StyleSheet.create({

});
```













