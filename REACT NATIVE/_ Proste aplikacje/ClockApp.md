[[biblioteka Moment Javascript]]

1. `npx create-expo-app ClockApp`
2. 
```bash
cd ClockApp
npm install moment react-moment
```
3. 

```jsx
import React, { useState, useEffect } from 'react';
import { View, Text, StyleSheet } from 'react-native';
import Moment from 'react-moment';
import moment from 'moment';

const ClockApp = () => {
  const [time, setTime] = useState(moment());

  useEffect(() => {
    const interval = setInterval(() => setTime(moment()), 1000);
    return () => clearInterval(interval);
  }, []);

  return (
    <View style={styles.container}>
      <Text style={styles.text}>
        <Moment element={Text} format="HH:mm:ss">{time}</Moment>
      </Text>
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1
    , justifyContent: 'center'
    , alignItems: 'center'
    , backgroundColor: '#999'
    ,
  },
  text: {
    fontSize: 50,
  },
});
export default ClockApp;
```
