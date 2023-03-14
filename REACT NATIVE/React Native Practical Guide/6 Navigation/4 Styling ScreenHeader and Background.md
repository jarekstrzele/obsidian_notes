[[_ 0 React Native Navigation]]

The  title in the screen comes from `name` attribute (it is a default header)
```jsx
<Stack.Screen name="MealsCategories"
              component={CategoriesScreen} />
```
https://reactnavigation.org/docs/native-stack-navigator#options

add `options={ { } }`

for one screen
```jsx 

export default function App() {
  return (
    <>
    <StatusBar style="dark" />
    <NavigationContainer>
      <Stack.Navigator>
        <Stack.Screen name="MealsCategories"
          component={CategoriesScreen}
          options={{
           title:'All Categories',
           headerStyle: { backgroundColor: "#991410" },
                          headerTintColor: "white",
                          contentStyle: { backgroundColor: '#3f2f'}
                           }
                          }
                        />
          <Stack.Screen name="MealsOverview"
                        component={MealsOverviewScreen}
                        />
        </Stack.Navigator>
      </NavigationContainer>
    </>
   );
}
```

for all screens
```jsx
  
export default function App() {
  return (
    <>
      <StatusBar style="dark" />
      <NavigationContainer>
        <Stack.Navigator
          screenOptions={{
            contentStyle: { backgroundColor: '#3f2f'},    
            headerStyle: { backgroundColor: '#991410' },
            headerTintColor: "white",
          }}
        >
          <Stack.Screen name="MealsCategories"
                        component={CategoriesScreen}
                        options={{
                          title:'All Categories',
                           }
                          }
                        />
          <Stack.Screen name="MealsOverview"
                        component={MealsOverviewScreen}
                        />
        </Stack.Navigator>
      </NavigationContainer>
    </>

   );

}
```


## Setting Navigation Options Dynamically
App.jsx
```jsx
//... each registered Screen has route, navigation
<Stack.Screen 
  name="MealsOverview"
  component={MealsOverviewScreen}
  options={ ( {route, navigation }) => {
          const catId = route.params.categoryId;

		  return {
             title: catId,
            }
      }}
/>
        </Stack.Navigator>
      </NavigationContainer>
    </>
```

Alternative way
`navigation` object has also `setOption()` method that takes an object to styling 

### with `useEffect`
[[useEffect]]

MealsOverviewScreen
```jsx
import {useEffect} from 'react';
import { View, FlatList, StyleSheet } from "react-native";
import { MEALS, CATEGORIES } from "../data/dummy-data";
import MealItem from "../components/MealItem";
 

function MealsOverviewScreen(props){

    const catId = props.route.params.categoryId;
    const displayedMeals = MEALS.filter((mealItem) => {
        return mealItem.categoryIds.indexOf(catId) >= 0;
    });

    useEffect( () => {
        const categoryTitle = CATEGORIES.find( (category) => category.id === catId).title;
        props.navigation.setOptions({
            title: categoryTitle
        });
        props.navigation.setOptions({
            title: categoryTitle
        });
}, [catId, navigator])
```




### or with `useLayoutEffect`
[[useLayoutEffect]]
```jsx
import {useLayoutEffect} from 'react';
import { View, FlatList, StyleSheet } from "react-native";
import { MEALS, CATEGORIES } from "../data/dummy-data";
import MealItem from "../components/MealItem";

function MealsOverviewScreen(props){

    const catId = props.route.params.categoryId;
    const displayedMeals = MEALS.filter((mealItem) => {
        return mealItem.categoryIds.indexOf(catId) >= 0;
    });

    useLayoutEffect( () => {
        const categoryTitle = CATEGORIES.find( (category) => category.id === catId).title;
        props.navigation.setOptions({
            title: categoryTitle
        });

        props.navigation.setOptions({
            title: categoryTitle
        });
}, [catId, navigator])
```

Hooki `useEffect` i `useLayoutEffect` w React.js pozwalają na wykonywanie określonych działań podczas cyklu życia komponentu. Główna różnica między nimi polega na tym, kiedy są wywoływane.

`useEffect` jest wywoływany asynchronicznie po aktualizacji drzewa renderującego i nie blokuje renderowania. Oznacza to, że kod zawarty w hooku `useEffect` może być wykonany po tym, jak komponent został zrenderowany. Jest to zazwyczaj stosowane do wykonywania działań pobocznych, takich jak pobieranie danych z serwera, manipulowanie DOM lub rejestrowanie zdarzeń.

Z drugiej strony, `useLayoutEffect` jest wywoływany synchronicznie zaraz po tym, jak React zakończy wykonywanie wszystkich obliczeń i gotowy jest do przeprowadzenia malowania (painting) i aktualizacji widoku (layout). Oznacza to, że kod zawarty w `useLayoutEffect` może być wykonany przed renderowaniem widoku i przed tym, jak użytkownik zobaczy efekty. Jest to zazwyczaj stosowane do wykonywania działań synchronicznych, takich jak modyfikowanie stylów lub manipulowanie rozmiarem elementów.

Podsumowując, `useEffect` jest wywoływany asynchronicznie, po zakończeniu aktualizacji widoku, a `useLayoutEffect` jest wywoływany synchronicznie, przed renderowaniem widoku. Wybór między nimi zależy od konkretnego przypadku użycia i celu, jaki chcesz osiągnąć.

----------------













