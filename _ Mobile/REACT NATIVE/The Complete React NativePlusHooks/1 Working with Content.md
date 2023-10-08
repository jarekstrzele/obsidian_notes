
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
import { Text, StyleSheet } from "react-native";

const ComponentsScreen = () => {
  return <Text style={styles.textStyle}>This is the components screen</Text>;
};

const styles = StyleSheet.create({
  textStyle: {
    fontSize: 30,
  },
});

export default ComponentsScreen;
```


mmon Questions and Answers








# Rules of JSX



# One Common Error




















