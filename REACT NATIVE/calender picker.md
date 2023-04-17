#react_native 

`npx create-expo-app calender-picker`

`npm install --save reat-native-calenders`
https://www.npmjs.com/package/react-native-calendars


```js
import { StatusBar } from 'expo-status-bar';
import { useState } from 'react';
import { StyleSheet, Text, View } from 'react-native';
import { Calendar } from 'react-native-calendars';
  

export default function App() {

  const [selectedDate, setSelectedDate] = useState('');

  function dataSelectionHandler(day){
    setSelectedDate(day.dateString) ;
    console.log(selectedDate) ;
  }


 // markedDates={ { [ss]: {selected: true}} } --> `[nazwaZmienna]` jak klucz; dynamiczne tworzenie kluczy
 // makred: true dodaje kropkę

 const ss = '2023-04-02' ;

  return (
    <View style={styles.container}>
      <Calendar
        onDayPress={ dataSelectionHandler }
        markedDates={ { [ss]: {selected: true, marked: true}, "2023-04-10": {marked: true}, "2023-04-18": {marked:true, dotColor: 'green'}} }
        />
    </View>
  );
}
 

const styles = StyleSheet.create({

  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
});
```

Oprócz podstawowego atrybutu `selected` do obiektu określającego oznaczenia daty w atrybucie `markedDates`, istnieją inne właściwości, które można wykorzystać do dodatkowej stylizacji oznaczeń. Oto niektóre z najczęściej używanych właściwości `markedDates`:

-   `selected` - ustawienie na `true` spowoduje wyświetlenie daty jako wybranej. Domyślnie, tło będzie miało kolor niebieski.
-   `marked` - ustawienie na `true` spowoduje oznaczenie daty kropką. Domyślnie, kropka będzie miała kolor niebieski.
-   `dotColor` - ustawienie koloru kropki (lub innej ikony), która ma być wyświetlana obok daty.
-   `selectedColor` - ustawienie koloru tła dla wybranej daty.
-   `selectedTextColor` - ustawienie koloru tekstu dla wybranej daty.
-   `disabled` - ustawienie na `true` spowoduje zablokowanie wybranej daty, dzięki czemu nie będzie można jej wybrać. Domyślnie, tło będzie miało kolor szary.
-   `disableTouchEvent` - ustawienie na `true` spowoduje zablokowanie zdarzenia dotknięcia na wybranej dacie.
-   `disableHighlight` - ustawienie na `true` spowoduje, że data nie będzie podświetlana, gdy zostanie najechana kursorem.









