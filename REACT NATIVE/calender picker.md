#react_native 

`npx create-expo-app calender-picker`

`npm install --save reat-native-calenders`
https://www.npmjs.com/package/react-native-calendars


```jsx
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
        markedDates={ {
              [selectedDate]: {selected: true, selectedTextColor: 'red'} ,
              [ss]: {selected: true, marked: true},
              "2023-04-10": {marked: true},
              "2023-04-18": {marked:true, dotColor: 'green'},
              "2023-04-22": {selected: true, marked: true, selectedTextColor: 'orange', selectedColor: 'blue'},
              "2023-04-01": {disableTouchEvent: true}
            } }
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


Oprócz atrybutu `markedDates`, komponent `Calendar` w bibliotece `react-native-calendars` posiada wiele innych atrybutów, które pozwalają na konfigurację wyglądu kalendarza i jego funkcjonalności. Oto kilka najważniejszych atrybutów komponentu `Calendar`:

-   `onDayPress` - funkcja, która jest wywoływana, gdy użytkownik naciśnie na daną datę. W argumencie przekazywana jest obiekt zawierający informacje o dacie.
-   `onDayLongPress` - funkcja, która jest wywoływana, gdy użytkownik długo naciśnie na daną datę. W argumencie przekazywana jest obiekt zawierający informacje o dacie.
-   `onMonthChange` - funkcja, która jest wywoływana, gdy użytkownik przewija kalendarz do innej miesiąca. W argumencie przekazywana jest data pierwszego dnia nowego miesiąca.
-   `current` - data, która ma być ustawiona jako początek wyświetlanego miesiąca. Domyślnie jest to bieżący miesiąc.
-   `minDate` - najwcześniejsza dozwolona data, która może zostać wybrana przez użytkownika.
-   `maxDate` - najpóźniejsza dozwolona data, która może zostać wybrana przez użytkownika.
-   `hideExtraDays` - ustawienie na `true` spowoduje ukrycie dni poprzedzających i następujących po miesiącu w wyświetlanym kalendarzu.
-   `disableMonthChange` - ustawienie na `true` spowoduje zablokowanie zmiany miesiąca.
-   `firstDay` - liczba reprezentująca pierwszy dzień tygodnia w kalendarzu. Domyślnie jest to niedziela (0).
-   `monthFormat` - formatowanie nazwy miesiąca w nagłówku kalendarza.
-   `disableArrowLeft` - ustawienie na `true` spowoduje ukrycie strzałki do przewijania miesiąca w lewo.
-   `disableArrowRight` - ustawienie na `true` spowoduje ukrycie strzałki do przewijania miesiąca w prawo.

Przykładowy kod, który wykorzystuje niektóre z powyższych atrybutów:






