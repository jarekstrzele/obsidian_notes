Go to App.js > look at the options in `<Stack.Screen`

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
go to your component (e.g. MealDetailScreen.js)










