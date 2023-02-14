
>[!info] Navigation
> 



```
npx create-expo-app FirstNavig
cd AwesomeProject  
npx expo start
```

# First nav app with dishes
new folders: 
- component
	- CategoryGridTitle.jsx
- data
	- dummy-data.js (Obisidian doesm't see it)
- models
	- category.js  (Obisidian doesm't see it)
	- meal.js  (Obisidian doesm't see it)
	- 
- screens
	- CategoriesScreen.jsx

`CategoriesScreen.jsx`
[[1.4. FlatList]]
```jsx
import { FlatList } from "react-native";
import CategoryGridTitle from "../components/CategoryGridTitle";
import { CATEGORIES } from "../data/dummy-data";

const renderCategoryItem = (itemData) => {
    return <CategoryGridTitle title={itemData.item.title}
                              color={itemData.item.color} />;
}
  

function CategoriesScreen(){
    return <FlatList data={CATEGORIES}
                     keyExtractor={(item)=> item.id}
                     renderItem={renderCategoryItem} />
}

export default CategoriesScreen
```


`CategoryGridTitle.jsx`
```jsx
import {Pressable, View, Text } from 'react-native';
const CategoryGridTitle = ({title, color}) => {
        return <View>
                <Pressable>
                    <View>
                        <Text>
                            {title}
                        </Text>
                    </View>
                </Pressable>
              </View>
}
export default CategoryGridTitle;
```


`App.jsx`
```jsx
import { StyleSheet, Text, View } from 'react-native';
import CategoriesScreen from './screens/CategoriesScreen';


export default function App() {
  return (
    <CategoriesScreen />
  );
}
const styles = StyleSheet.create({
  container: {
  },
});
```


##  Some styling
to change background color in all app:
- go to `app.json`
- `expo`> add `backgroundColor: new value`
- reload


CategoryGridTitle.jsx
```jsx
import {Pressable, View, Text, StyleSheet, Platform } from 'react-native';

const CategoryGridTitle = ({title, color}) => {
        return <View style={styles.outerView}>
                <Pressable  style={ ({pressed}) => [styles.pressableView, pressed ? styles.pressedButton : null] }                       android_ripple={{color:'#ccc'}}>
<View style={[styles.innerView, , {backgroundColor: color}]}>
      <Text style={styles.title}>
            {title}
      </Text>
</View>
</Pressable>
</View>
}

export default CategoryGridTitle;
const styles = StyleSheet.create({
    outerView: {
        flex: 1,
        margin: 16,
        height:150,
        // borderRadius: 18,
        elevation: 6,
        backgroundColor: 'white',
        shadowColor: 'black',
        shadowOpacity: 0.25,
        shadowOffset: { width: 0, height: 2},
        shadowRadius: 8,
        overflow: Platform.OS === 'android'? 'hidden' : 'visible'
    },
    pressableView:{
        flex: 1
    },
    pressedButton: {
        opacity: 0.5
    },

    innerView: {
        flex: 1,
        padding: 16,
        justifyContent: 'center',
        alignItems: 'center',
        borderRadius: 18,
    },
    title:{
        fontWeight: 'bold',
        fontSize: 18
    }
});

// you have to add button style to Pressable
// because without that style Pressable is empty, so it takes no place, so text will not be visible
//
// F O R    i O S   !!!!!!!!!!!!!!!!!!
// backgroundColor: 'white',
// shadowColor: 'black',
// shadowOpacity: 0.25,
// shadowOffset: { width: 0, height: 2},
// shadowRadius: 8,
// press effect -> on Android `android_ripple={{color:'#ccc'}}`
// add overflow: 'hidden' ripple will not go beyong the rounded corners, but it can remove some effect from iOS
// so you Platform.OS
// initially <Pressable style={style.button} .. but to make ripple effect in iOS you have to make some other changes
// initially   return <View style={styles.outerView}>
// but now  return <View style={[styles.outerView, {backgroundColor: color}]}>
// to make some better ripple effect on iOS
```


App.jsx
```jsx
import { StatusBar } from 'expo-status-bar';
import { StyleSheet, Text, View } from 'react-native';
import CategoriesScreen from './screens/CategoriesScreen';

export default function App() {
  return (
    <>
    <StatusBar style='light' />
     <CategoriesScreen />
    </>
  );
}
  
const styles = StyleSheet.create({
  container: {
  },
});
```


---
## Add some action React Navigator
https://reactnavigation.org/
#reactnavigation 

##  1. `npm install @react-navigation/native`
## 2. `npx expo install react-native-screens react-native-safe-area-context`
## 3. `import {} from '@react-navigation/native'` ;`

**on web reactnavigation -> API Reference > Navigators**

## Stack navigator
`npm install @react-navigation/native-stack`


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
## second screen
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

this `navigation` allow to navigate between screens
the **navigation** object has a method `navigate()` to which pass a name of a page you want to navigate (use the value of `name` attribute e.i. 
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



# Working 
in MealsOverviewScreen.jsx (object `route` as props)
```jsx
import { View, Text, StyleSheet } from "react-native";
import { MEALS } from "../data/dummy-data";

function MealsOverviewScreen(props){

	const catId = props.route.params.categoryId;
    return(
        <View style={styles.container}>
            <Text>Meals Overview Screen - {catId} </Text>
        </View>
    )
}
```


------------------

MealsOverViewScreen.jsx
```jsx
import { View, Text, StyleSheet } from "react-native";

import { MEALS } from "../data/dummy-data";

  

function MealsOverviewScreen(props){

  

 const catId = props.route.params.categoryId;

  

    return(

        <View style={styles.container}>

            <Text>Meals Overview Screen - {catId} </Text>

        </View>

    )

}

  

export default MealsOverviewScreen ;

  

const styles = StyleSheet.create({

    container: {

        flex:1,

        padding: 16 ,

    }

})
```


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

                                  whenPressExecute={() => { props.navigation.navigate("MealsOverview", {

                                    categoryId: itemData.item.id,

                                  }) } } />;

    }

  

    return <FlatList data={CATEGORIES}

                     keyExtractor={(item)=> item.id}

                     renderItem={renderCategoryItem}

                     numColumns={2}/>

  

}

  

export default CategoriesScreen

  

// numColumns={2} in two columns
```

CategoryGridTitle.jsx
```jsx
import {Pressable, View, Text, StyleSheet, Platform } from 'react-native';

const CategoryGridTitle = ({title, color, whenPressExecute}) => {

        return <View style={styles.outerView}>
                <Pressable  style={ ({pressed}) => [styles.pressableView,
                                                    pressed ? styles.pressedButton : null] }
                            android_ripple={{color:'#ccc'}}
                            onPress={whenPressExecute}>
                    <View style={[styles.innerView, , {backgroundColor: color}]}>
                        <Text style={styles.title}>
                            {title}
                        </Text>
                    </View>
                </Pressable>
              </View>
}

export default CategoryGridTitle;

const styles = StyleSheet.create({
    outerView: {
        flex: 1,
        margin: 16,
        height:150,
        // borderRadius: 18,
        elevation: 6,
        backgroundColor: 'white',
        shadowColor: 'black',
        shadowOpacity: 0.25,
        shadowOffset: { width: 0, height: 2},
        shadowRadius: 8,
        overflow: Platform.OS === 'android'? 'hidden' : 'visible'
    },
    pressableView:{
        flex: 1
    },
    pressedButton: {
        opacity: 0.5
    },
    innerView: {
        flex: 1,
        padding: 16,
        justifyContent: 'center',
        alignItems: 'center',
        borderRadius: 18,
    },
    title:{
        fontWeight: 'bold',
        fontSize: 18
    }
});

// you have to add button style to Pressable
// because without that style Pressable is empty, so it takes no place, so text will not be visible
//
// F O R    i O S   !!!!!!!!!!!!!!!!!!
// backgroundColor: 'white',
// shadowColor: 'black',
// shadowOpacity: 0.25,
// shadowOffset: { width: 0, height: 2},
// shadowRadius: 8,
// press effect -> on Android `android_ripple={{color:'#ccc'}}`
// add overflow: 'hidden' ripple will not go beyong the rounded corners, but it can remove some effect from iOS
// so you Platform.OS
// initially <Pressable style={style.button} .. but to make ripple effect in iOS you have to make some other changes
// initially   return <View style={styles.outerView}>
// but now  return <View style={[styles.outerView, {backgroundColor: color}]}>
// to make some better ripple effect on iOS
```

















