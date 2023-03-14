#react_native/drawer_navigation
https://reactnavigation.org/docs/drawer-navigator

1.
### `npm install @react-navigation/drawer`

2.
### `npx expo install react-native-gesture-handler react-native-reanimated`

3.
### `import 'react-native-gesture-handler';`


## ==problem z react-native-reanimated==
### `npm install react-native-reanimated@1 --save --save-exact`


App.jsx
```jsx
import { StatusBar } from 'expo-status-bar';
import { StyleSheet, Text, View } from 'react-native';
import { NavigationContainer } from '@react-navigation/native' ;
import { createDrawerNavigator } from '@react-navigation/drawer';
import WelcomeScreen from './screens/WelcomeScreen' ;
import UserScreen from './screens/UserScreen';
import 'react-native-reanimated';
  

const Drawer = createDrawerNavigator() ;
  

export default function App() {
return (


<NavigationContainer>

<Drawer.Navigator>

<Drawer.Screen name="Welcome" component={WelcomeScreen} />

<Drawer.Screen name="User" component={UserScreen} />

</Drawer.Navigator>

</NavigationContainer>

);

}
```


UserScreen
```jsx
import { View, Text , StyleSheet} from 'react-native' ;

function UserScreen(){

return (
<View style={styles.rootContainer}>
<Text>
This is the <Text style={styles.highlight}> User am I </Text> screen!
</Text>
</View>
) ;
}

export default UserScreen ;

const styles = StyleSheet.create({
rootContainer:{
flex: 1,
justifyContent: 'center',
alignItems: 'center'
},
highlight: {

color: 'green'

}

})
```


WelcomeScreen.jsx
```jsx
import {View, Text, StyleSheet } from 'react-native' ;

function WelcomeScreen() {
	return (
		<View style={styles.rootContainer}>
			<Text>
				This is the <Text style={styles.highlight}> WELCOME, Zdrastwójcie </Text> screen!
			</Text>
		</View>
)
	}

  
export default WelcomeScreen;

const styles = StyleSheet.create({
rootContainer:{
flex: 1,
justifyContent: 'center',
alignItems: 'center',
},
highlight: {
color: 'red'
}
})
```

App
```jsx
const Drawer = createDrawerNavigator() ;

  

export default function App() {
	return (
	<NavigationContainer>
		<Drawer.Navigator>
		<Drawer.Screen name="Welcome" component={WelcomeScreen}
	options={{ headerStyle: { backgroundColor: '#1c0a66'},
	headerTintColor:'white',
	drawerLabel: 'WelcomeLable Screen',
	drawerActiveBackgroundColor: '#fae',
	drawerActiveTintColor: '#3c0a6b',
	drawerStyle: { backgroundColor: '#ccc'}
	}} />

		<Drawer.Screen name="User" component={UserScreen} />
	</Drawer.Navigator>
</NavigationContainer>

);

}
```

if you add some of these styles to `Drawer.Navigator` they will be affected all screen


UserScreen.jsx
```jsx
import { View, Text , StyleSheet, Button} from 'react-native' ;

  

function UserScreen(props){

  

function openDrawerHandler(){

props.navigation.toggleDrawer();

}

  

return (

<View style={styles.rootContainer}>

<Text>

This is the <Text style={styles.highlight}> User am I </Text> screen!

</Text>

<Button title="pen Drawer" onPress={openDrawerHandler} />

</View>

) ;

}

  

export default UserScreen ;

  
  
  

const styles = StyleSheet.create({

rootContainer:{

flex: 1,

justifyContent: 'center',

alignItems: 'center'

},

highlight: {

color: 'green'

}

})
```


WelcomeScren
```jsx
import {View, Text, StyleSheet } from 'react-native' ;

  

function WelcomeScreen() {

return (

<View style={styles.rootContainer}>

<Text>

This is the <Text style={styles.highlight}> WELCOME, Zdrastwójcie </Text> screen!

</Text>

</View>

)

}

  

export default WelcomeScreen;

  
  

const styles = StyleSheet.create({

rootContainer:{

flex: 1,

justifyContent: 'center',

alignItems: 'center',

},

highlight: {

color: 'red'

}

})

```

App
```jsx
import { StatusBar } from 'expo-status-bar';

import { StyleSheet, Text, View } from 'react-native';

import { NavigationContainer } from '@react-navigation/native' ;

import { createDrawerNavigator } from '@react-navigation/drawer';

import WelcomeScreen from './screens/WelcomeScreen' ;

import UserScreen from './screens/UserScreen';

import 'react-native-reanimated';

import { Ionicons } from '@expo/vector-icons' ;

  

const Drawer = createDrawerNavigator() ;

  

export default function App() {

return (

<NavigationContainer>

<Drawer.Navigator

screenOptions={{

drawerActiveBackgroundColor: '#fae',

drawerActiveTintColor: '#3c0a6b',

drawerStyle: { backgroundColor: '#ccc'},

headerStyle: { backgroundColor: '#1c0a66'},

headerTintColor:'white'

}}

>

<Drawer.Screen name="Welcome" component={WelcomeScreen}

options={{

drawerLabel: 'WelcomeLable Screen' ,

drawerIcon: ({color, size}) => <Ionicons name="home" color={color} size={size} />

}}

/>

<Drawer.Screen name="User" component={UserScreen}

options={{

drawerIcon: ({ color, size }) => (

<Ionicons name="person" color={color} size={size} />

)

}}

/>

</Drawer.Navigator>

</NavigationContainer>

);

}

```


----------
# Button Tabs
https://reactnavigation.org/docs/bottom-tab-navigator

## `npm install @react-navigation/bottom-tabs`

```jsx
import { NavigationContainer } from '@react-navigation/native' ;

// import { createDrawerNavigator } from '@react-navigation/drawer';

import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';

  
  
  

import WelcomeScreen from './screens/WelcomeScreen' ;

import UserScreen from './screens/UserScreen';

import 'react-native-reanimated';

import { Ionicons } from '@expo/vector-icons' ;

  

// const Drawer = createDrawerNavigator() ;

const BottomTab = createBottomTabNavigator();

  
  

export default function App() {

return (

<NavigationContainer>

<BottomTab.Navigator

screenOptions={{

headerStyle: { backgroundColor: '#445566'},

headerTinColor: 'white'

}}

>

<BottomTab.Screen name="Welcome" component={WelcomeScreen}

options={{

tabBarIcon: ({color, size}) => (<Ionicons name="home" color={color} size={size} />) ,

}}

/>

<BottomTab.Screen name="User" component={UserScreen}

options={{

tabBarIcon: ({color, size}) => (<Ionicons name="person" color={color} size={size} />) ,

}}

/>

</BottomTab.Navigator>

</NavigationContainer>

);

}
```





