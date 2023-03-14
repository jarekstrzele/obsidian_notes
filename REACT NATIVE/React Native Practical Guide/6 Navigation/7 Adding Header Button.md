Go to App.js > look at the options in `<Stack.Screen`
[[_ 0 React Native Navigation]]


# WITHOUT direct communication with component
e.g.

```jsx
//...
<Stack.Screen
	name="MealDetail"
	component={MealDetailScreen}
	options={{
		headerRight: () = {
			return <Text> In the header </Text>
		}
	}}
	/>
```


other
```jsx
headerLeft: () = {
			return <Text> In the header </Text>
		}
```

or
```jsx
//..
	return <Button title="Tap me" onPress={...} />
```


-------------
# with direct interaction
go to your component (e.g. MealDetailScreen.js) and use `useLayoutEffect` and `setOptions` method

1. `import { useLayoutEffect } from 'react' ;`
2. use `navigation`
```jsx
function MealDetailScreen({route, navigation}) {
//...

	function headerButtonPressHandler(){
	}


useLayoutEffect( () => {
 navigation.setOptions({
	 headerRight: () => {
		 return <Button title="Tap me" onPress={headerButtonPressHandler}/>
	 }
 }) ;
}, [navigation, headerButtonPressHandler])
	

return (
//...
)



}
```










