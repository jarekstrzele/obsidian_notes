[[_ 0 React Native Navigation]]

 You can create a new component
 
```jsx
import { Pressable } from  'react-native' ;
import { Iconicons } from '@expo/vector-icons' ;

function IconButton(props){
return (
	<Pressable onPress={props.o}>
		<Ionicons name="star" size={24} color="white" />
	</Pressable>
)
}

export default IconButton
```










