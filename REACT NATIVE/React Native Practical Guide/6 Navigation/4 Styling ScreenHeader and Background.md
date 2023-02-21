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
//...
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



