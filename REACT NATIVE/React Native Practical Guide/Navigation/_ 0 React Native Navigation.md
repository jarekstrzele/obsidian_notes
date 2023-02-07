
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


# Some styling
to change background color in all app:
- go ro `app.json`
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
# Add some action React Navigator
https://reactnavigation.org/
#reactnavigation 

##  1. `npm install @react-navigation/native`
## 2. `npx expo install react-native-screens react-native-safe-area-context`
## 3. `import {} from '@react-navigation/native'` ;`














