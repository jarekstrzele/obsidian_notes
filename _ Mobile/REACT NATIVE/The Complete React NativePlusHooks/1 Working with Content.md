
# Overview of React Components


------------
## React Component File

**Component files create and export exactly one React Component**

```jsx
`import LIBRARIES we need to create a component`

`Create a COMPONENT - a function that retirns some 'JSX'`

`Create a STYLESHEET to style our component`

`EXPORT the component so we can use it elsewhere in our project`
```

>[!info] Text
>a 'primitive' React element. Used to show some basic content on the screen

>[!info] View
>general purpose element used for grouping other elements or styling

>[!info] Image 
>show an image

>[!info] Button
>show a button the user can press. Gives us some feedback whenever the user presses it



>[!info] JSX
>it is a 'dialect' of JS that tells React what content we want to show

>[!info] AppNavigator
>it is a tool from a library called 'React Navigation' that is used to show different screens to the user

>[!info] StyleSheet.create()
>It is a functiona that validates a set of styling rules that we pass into it

```jsx
import React from "react";
import { Text, StyleSheet, View } from "react-native";

const ComponentsScreen = () => {
  return (
  <View>
	  <Text style={styles.textStyle}>This is the components screen</Text>
	  <Text> Second text </Text>
  </View>
)};

const styles = StyleSheet.create({
  textStyle: {
    fontSize: 30,
  },
});

export default ComponentsScreen;
```



# Rules of JSX
- we can assemble different JSX elements like normal HTML
- we configure different JSX elements using "propsS"
- we can refer to JS variables inside of a JSX block by using curly braces
- we can assign JSX elements to a variable, then show that variable inside of a JSX block

```jsx
import React from "react";
import { Text, StyleSheet, View } from "react-native";

const ComponentsScreen = () => {
  const greetings = "Hello from the component";
  const secondGreetings = <Text>New text from variable</Text>;

  return (
    <View>
      <Text style={styles.textStyle}>This is the components screen</Text>
      <Text>{greetings}</Text>
      {secondGreetings}
    </View>
  );
};

const styles = StyleSheet.create({
  textStyle: {
    fontSize: 30,
  },
});

export default ComponentsScreen;
```

# One Common Error

wrong
```js
//...
return;
<Text> ... </Text>
```


correct
```jsx
//....
return (
	<Text>...</Text>
);
```















