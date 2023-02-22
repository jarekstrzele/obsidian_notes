[[biblioteka Moment Javascript]]

1. `npx create-expo-app ClockApp`
2. 
```bash
cd ClockApp
npm install moment react-moment
```

---
`setInterval`
Funkcja ta przyjmuje dwa argumenty: 
 - funkcję, która ma zostać wywołana co określony czas (w tym przypadku funkcja `setTime(moment())`, która ustawia aktualny czas za pomocą biblioteki Moment) oraz
 - czas w milisekundach (1000 milisekund to 1 sekunda).

----
`moment()`
zwraca obiekt *Moment* reprezentujący aktualny czas, tzn. czas w momencie wywołania tej funkcji.
Obiekt Moment jest obiektem daty i czasu

---
`clearInterval`
Funkcja zwracana przez `useEffect` jest opcjonalna i umożliwia czyszczenie efektów ubocznych wykonanych przez funkcję `useEffect`. Dzięki temu, jeśli w komponencie funkcyjnym została utworzona subskrypcja, ustawiony czasomierz lub jakikolwiek inny efekt uboczny, to można usunąć ten efekt przy usuwaniu komponentu, aby uniknąć wycieków pamięci.

W powyższym kodzie, funkcja zwracana przez `useEffect` zawiera wywołanie funkcji `clearInterval`, która zatrzymuje czasomierz i zapobiega wyciekom pamięci. Dzięki temu, kiedy komponent jest usuwany, czasomierz jest zatrzymywany i nie będzie dalej działał.

Jeśli nie zastosowano by tej funkcji zwracającej, to czasomierz kontynuowałby działanie po usunięciu komponentu, co mogłoby prowadzić do wycieków pamięci lub innych problemów w aplikacji. Dlatego jest to dobry nawyk, aby w `useEffect` zawsze czyszczać efekty uboczne, takie jak subskrypcje lub ustawione czasomierze.

----

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
