[[_ 0 React Native Navigation]]

install navigator [[Drawer Navigator]]

add (in App.js):
```jsx
//...
import {createDrawerNavigator} from '@react-navigation/native-stack';

const Drawer = createDrawerNavigator();

function DrawerNavigator(){
 return <Drawer.Navigator
	screenOptions={{
		headerStyle: ...
		sceneContainerStyle: {backgroundColor: ''}
	}} 
>
	<Drawer.Screen name="Categories" 
		component={CateriesScreen}/>
	<Drawer.Screen name="Categories" 
		component={NewDummyComponentScreen}/>
									
</Drawer.Navigator>
}

function App(){
//../

<Stack.Screen 
	name="DrawerScreen" 
	//component={CateriesScreen}
	component={DrawerNavigator}
	options={{
		title: 'All Categories',
		headerShown: false
	}}
```


--------------

```jsx
import { NavigationContainer } from '@react-navigation/native' ;
import { Ionicons } from '@expo/vector-icons';
// it creates an object with two properties Navigator and Screen (to register a screen that will be managed by this navigator)
// where every property hodls an object that acts as a component
const Stack = createNativeStackNavigator() ;
const Drawer = createDrawerNavigator();

function DrawerNavigator(){

return (
<Drawer.Navigator
 screenOptions={{
	sceneContainerStyle: { backgroundColor: '#3f2f5'},
	headerStyle: { backgroundColor: '#991410' },
	headerTintColor: "white",
	drawerContentStyle : {backgroundColor: '#991410'},
	drawerInactiveTintColor: 'white',
	drawerActiveBackgroundColor: '#3c1000',
	drawerActiveTintColor: 'white'
	}}
>

<Drawer.Screen 
 name="Categories" 
 component={CategoriesScreen}
 options={{
  title: 'All categories',
  drawerIcon: ({color, size}) => <Ionicons name="list-circle" color={color} size={size} />
}}/>

<Drawer.Screen 
 name="Favorites"
 component={FavoriteScreen}
 options={{
  title: "My Favorite !!",
  drawerIcon: ({color, size}) => (
<Ionicons name="star" color={color} size={size} />
)
}}
/>
</Drawer.Navigator>)
}

export default function App() {

return (
```







