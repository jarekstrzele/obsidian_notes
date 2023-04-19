#react_native 

`npx create-expo-app calender-picker`

## `npm install --save reat-native-calendars`
https://www.npmjs.com/package/react-native-calendars

# Calendar

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

----
# CalendarList
jest jak FlatList (renderuje tylko to co widoczne)

> `SafeAreaView` jest ważnym narzędziem do tworzenia interfejsu użytkownika w React Native, zapewniającym, że wyświetlana treść będzie dobrze widoczna na ekranie i nie będzie zakrywana przez elementy systemowe.


```jsx
import { StatusBar } from 'expo-status-bar';
import { useState } from 'react';
import { StyleSheet, Text, View, SafeAreaView } from 'react-native';
import { Calendar, CalendarList } from 'react-native-calendars';

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
    <SafeAreaView style={styles.container} >
      <View>
        <Text> Przykład dla komponentu CalendarList</Text>
      </View>
      <CalendarList
        current={'2023-03-01'}
        minDate={'2020-03-08'}
        maxDate={'2023-12-31'}
        onDayPress={dataSelectionHandler}
        markedDates={{
          [selectedDate]:{ selected: true}
        }}
  
        />

    </SafeAreaView>
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


-------
# Agenda
`Agenda` pozwala na dynamiczne wyświetlanie zawartości w kalendarzu, która dostosowuje się do zmian daty lub czasu. Komponent może wyświetlać listę wydarzeń, notatki, zadania lub inne informacje dla każdego dnia w kalendarzu. Możliwe jest także wyświetlanie informacji dla kilku miesięcy jednocześnie.

`Agenda` oferuje szereg funkcjonalności, w tym:

1.  Automatyczne przewijanie kalendarza w celu wyświetlenia kolejnych dni.
2.  Wbudowane filtrowanie i sortowanie wydarzeń na podstawie wybranej daty.
3.  Obsługa niestandardowych typów wydarzeń, takich jak wydarzenia cykliczne, wydarzenia z powtarzaniem czy wydarzenia całodniowe.
4.  Wbudowane stylowanie komponentów kalendarza za pomocą arkuszy stylów lub przekazywanie stylów jako propsy


```jsx
import { StatusBar } from 'expo-status-bar';

import { useState } from 'react';

import { StyleSheet, Text, View, SafeAreaView } from 'react-native';

import { Calendar, CalendarList, Agenda } from 'react-native-calendars';

  
  
  

export default function App() {

  

  const wydarzenia = {

    '2023-04-20': [ {opis: "praca klasowa 1", czas: '10:00 '}],

    '2023-04-21': [{ opis: 'Wyjście na lody 2', czas: '12:00 ' }],

    '2023-04-25': [{ opis: 'Sprawdzian z OOP 3', czas: '16:33 ' }, { opis: 'Wspólne granie 3', czas: '19:54 ' }],

 };

  

 function renderWydarzenia(wydarzenie){

  return (

    <View >
      <Text>{wydarzenie.opis}</Text>
      <Text>{wydarzenie.czas}</Text>
    </View>
  )
 }

  function renderEmptyDate(){
    return (
      <View>
       <Text>W tym dni nie ma nic do roboty</Text>
      </View>
    )
  }

  return (

  <Agenda

    items={wydarzenia}

    renderItem={renderWydarzenia}

    renderEmptyDate = {renderEmptyDate}

  />

  );

}

  

const styles = StyleSheet.create({

  container: {

    flex: 1,

    backgroundColor: '#fff',

    alignItems: 'center',

    justifyContent: 'center',

  },

});n 
```

















