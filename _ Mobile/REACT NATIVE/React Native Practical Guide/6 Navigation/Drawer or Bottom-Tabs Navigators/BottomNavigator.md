[[Drawer Navigator]]
#bottom_tabs


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





