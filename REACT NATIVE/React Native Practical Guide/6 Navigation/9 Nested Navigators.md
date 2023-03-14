[[_ 0 React Native Navigation]]

install navigator [[Drawer Navigator]]

add (in App.js):
```jsx
//...
import {createDrawerNavigator} from '@react-navigation/native-stack';

const Drawer = createDrawerNavigator();

function DrawerNavigator(){
 return <Drawer.Navigator>
	<Drawer.Screen name="Categories" 
					component={CateriesScreen}/>
</Drawer.Navigator>
}

function App(){
//../

<Stack.Screen 
	name="DrawerScreen" 
	//component={CateriesScreen}
	component={DrawerNavigator}
	options={{
		title: 'All Categories'
	}}
```
