#react_native/clock

### `npx expo install dayjs`


Wstęp komponent `<Clock />`
```jsx
import {Text, View, StyleSheet} from 'react-native';
import { useState } from 'react';
import dayjs from "dayjs" ;

function Clock(){

    const [time, setTime] = useState(new Date())

    return(
    <View style={styles.container}>
        <Text style={styles.date}> 04.04.2023</Text>
        <Text style={styles.time}>19:24</Text>
    </View>
    )
}
  

export default Clock;
 

const styles = StyleSheet.create({
    container:{
        fontFamily: 'Pacifico',
        backgroundColor: '#cab',
        alignItems: 'center',
        justifyContent: 'center',
        borderRadius: 5
    },
    data: {
        fontSize: 20,
    },
  

    time: {
        fontSize: 40
    }
})
```

som changes:
```jsx
 return(

    <View style={styles.container}>
        <Text style={styles.date}>{dayjs().format("dddd, DD MMMM")} 04.04.2023</Text>
        <Text style={styles.time}>{dayjs().format("hh:mm")}</Text>
    </View>

    )
```




