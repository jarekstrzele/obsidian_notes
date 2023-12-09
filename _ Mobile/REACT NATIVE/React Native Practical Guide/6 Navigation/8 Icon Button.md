[[_ 0 React Native Navigation]]

 You can create a new component
 
```jsx
import { Pressable } from  'react-native' ;
import { Iconicons } from '@expo/vector-icons' ;

function IconButton(props){
return (
	<Pressable onPress={props.onTap}>
		<Ionicons name={props.icon} size={24} color={props.color} />
	</Pressable>
)
}

export default IconButton
```

and in MEalDetailScreen.js
		look at [[7 Adding Header Button]]
```jsx
//....

	function headerButtonPressHandler(){
		console.log("Pressed") ;
	}


useLayoutEffect( () => {
 navigation.setOptions({
	 headerRight: () => {
		 return <IonButton 
			 onTap={headerButtonPressHandler}
			 color="white"
			 icon="star"
			 />
	 }
 }) ;
}, [navigation, headerButtonPressHandler])

//....

```








