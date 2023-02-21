 [[_ 0 React Native Navigation]]


# Install 
https://reactnavigation.org/
#reactnavigation 
[[_ 0 React Native Navigation]]

##  1. `npm install @react-navigation/native` - core react navigation packages

## 2. `npx expo install react-native-screens react-native-safe-area-context` - in your project directory

to use 
## 3. `import {} from '@react-navigation/native'` ;`

3.1. import `NavigationContainer` and wrap your components in that component
3.2. you will use `navigator-stack` to navigate
	**on web reactnavigation -> API Reference > Navigators**
	find navigator-stack
	**to install native stack navigator**
## `npm install @react-navigation/native-stack`

# Use
```jsx
import { StatusBar } from 'expo-status-bar';
import { StyleSheet, Text, View } from 'react-native';
import CategoriesScreen from './screens/CategoriesScreen';
import { createNativeStackNavigator } from '@react-navigation/native-stack' ; 

// it is only a container
import { NavigationContainer } from '@react-navigation/native' ;
// it creates an object with two properties Navigator and Screen (to register a screen that will be managed by this navigator)
// where every property  hodls an object that acts as a component
const Stack = createNativeStackNavigator() ;

export default function App() {
  return (
    <>
    <StatusBar style='dark' />
    <NavigationContainer>
      <Stack.Navigator>
        <Stack.Screen name="MealsCategories" component={CategoriesScreen}/>
      </Stack.Navigator>
    </NavigationContainer>
    </>
  );
}
```

--------
# Add a second screen
CategoriesScreen.jsx
```jsx
import { FlatList } from "react-native";
import CategoryGridTitle from "../components/CategoryGridTitle";
 

import { CATEGORIES } from "../data/dummy-data";
// move to inside to component Categories to have access to `props.navigation`
// const renderCategoryItem = (itemData) => {
//     function pressHandler(){
//     }
//     return <CategoryGridTitle title={itemData.item.title}
//                               color={itemData.item.color}
//                                whenPressExecute={pressHandler}/>;
// }


// props.navigation is special prop send by Navigator.Screen
function CategoriesScreen(props){
    function renderCategoryItem(itemData) {
        return <CategoryGridTitle title={itemData.item.title}
                                  color={itemData.item.color}
                                  whenPressExecute={() => { props.navigation.navigate("MealsOverview") } } />;
    }
 
    return <FlatList data={CATEGORIES}
                     keyExtractor={(item)=> item.id}
                     renderItem={renderCategoryItem}
                     numColumns={2}/>

}

export default CategoriesScreen
// numColumns={2} in two columns
```


App.js
```jsx
import { StatusBar } from 'expo-status-bar';
import { StyleSheet, Text, View } from 'react-native';
import CategoriesScreen from './screens/CategoriesScreen';
import MealsOverviewScreen from './screens/MealsOverviewScreen';
import { createNativeStackNavigator } from '@react-navigation/native-stack' ;
// // it is only a container
import { NavigationContainer } from '@react-navigation/native' ;

// it creates an object with two properties Navigator and Screen (to register a screen that will be managed by this navigator)
// where every property  hodls an object that acts as a component
const Stack = createNativeStackNavigator() ;

export default function App() {
  return (
    <>
      <StatusBar style="dark" />
      <NavigationContainer>
        <Stack.Navigator>
          <Stack.Screen name="MealsCategories"
                        component={CategoriesScreen}
                        />
          <Stack.Screen name="MealsOverview"
                        component={MealsOverviewScreen}
                        />
        </Stack.Navigator>
      </NavigationContainer>
    </>
   );
}

const styles = StyleSheet.create({
  container: {
  },
});

```

`component={CategoriesScreen}` -> this component will have special prop -> `props.navigtion` (all components register in `component` attribute have this prop)

- this `navigation` allow to navigate between screens
- the **navigation** object has a method `navigate()` to which pass a name of a page you want to navigate (use the value of `name` attribute e.i. 
```jsx
<Stack.Screen name="MealsOverview"
                        component={MealsOverviewScreen}
                        />
```
)

---------------
## Setting the Default Screen

When setting up a Navigator (like `<Stack.Navigator>`) and registering its screens (via `<Stack.Screen>`), you can decide **which screen will be shown as a default when the app starts**.

Out of the box, the **top-most screen** (i.e. the **first child** inside of `<Stack.Navigator>`) is used as the initial screen.

I.e., in the following example, the AllProducts screen would be shown as an initial screen when the app starts:

1.  <Stack.Navigator>
2.    <Stack.Screen name="AllProducts" component={AllProducts} /> // initial screen
3.    <Stack.Screen name="ProductDetails" component={ProductDetails} />
4.  </Stack.Navigator>

You can therefore change the initial screen by changing the `<Stack.Screen>` order. Alternatively, there also is an `initialRouteName` prop that can be set on the navigator component (i.e., on `<Stack.Navigator>` in this case):

1.  <Stack.Navigator initialRouteName="ProductDetails">
2.    <Stack.Screen name="AllProducts" component={AllProducts} /> 
3.    <Stack.Screen name="ProductDetails" component={ProductDetails} /> // initial screen
4.  </Stack.Navigator>

----
## `useNavigation()`
**When you want use Navigator but your component is not register like these**:
```jsx
<Stack.Navigator>
          <Stack.Screen name="MealsCategories"
                        component={CategoriesScreen}
                        />
          <Stack.Screen name="MealsOverview"
                        component={MealsOverviewScreen}
                        />
        </Stack.Navigator>
```

`import {useNavigation} from "@react-navigation/native"`
`const navigation = useNavigation()`

[[useNavigation Hook]]

-----------
## sending data by  `navigator`

CategoriesScreem.jsx (add object to `navigate` method)
```jsx
function CategoriesScreen(props){
    function renderCategoryItem(itemData) {
        return <CategoryGridTitle title={itemData.item.title}
                                  color={itemData.item.color}
                                  whenPressExecute={() => { props.navigation.navigate("MealsOverview", {
                                    categoryId: itemData.item.id,
                                  }) } } />;
    }
//...  

}
```

