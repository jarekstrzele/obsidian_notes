[https://snack.expo.dev](https://snack.expo.dev)
https://codesandbox.io

---
#udemy #Maximilian_Schwarzmuller #react_native 

----
[[1 React Native Basics]]
[[2 Debugging React Native Apps]]







---
# React Native Practical Guide
React.js + React Native -> Real Native Mobile Apps (iOS, Android)

React:
- itself is platform-agnostic
- it's actually react-dom that adds web support

React Native:
- a colletion of "special" React components (`<View> </View>`. `<Text> </Text>`... )
- Components are compiled to native UI elements
- React Native is like react-dom: it "connects" React to a specific platform


Web Browser (react-dom) | Native Component (Android) | Native Component (iOS) | React Native JSX
---|---|---|---
`<div>` | `android.View` | `UIView` | `<View>`
`<input>` | `EditText` | `UITextField` | `<TextInput>`
... | ... | ... | ...


>[!important] React Native
>It maps and compiles re-usable components to respective platform equivalents



## Logic?
Views are compiled to native views but logic not.
JavaScript thread, hosted by React Native (in the app)
JS code will be able to talk to the underlying native platform (iOS, Android) through a basic translation bridge


## To create project
www.reactnative.dev

(before you have to install Nodejs)
expo CLI Quickstart `npm install -g expo-cli`  (`-g` globally)
(you can use third-party service for free), expo is easier than React Native CLI (it is more advance)

#### `expo init AwesomeProject` - to start a new project
(choose blank a minimal app as clean as an empty canvas)

**What is inside of this project just created?**

`.expo-shared` some internal info
`assets` you can stor images there
`node_moduels` - all third-party packages
`package.json` lists all the dependencies of our project
`babel.config.js` how code is translate under the hood
`app.json` here we can configure some settings  and behaviers of our react-native app; this file will be picked up by expo  when our app is build for preview or for the actual app stores
`App.js` this is the only real code file we have in this started project

App.js:
```jsx
import * as React from 'react';
import { Text, View, StyleSheet } from 'react-native';
import Constants from 'expo-constants';
import { StatusBar } from 'expo-status-bar';

// You can import from local files
import AssetExample from './components/AssetExample';

// or any pure javascript modules available in npm
import { Card } from 'react-native-paper';
export default function App() {
	return (
<View style={styles.container}>
	<Text> Open up APp.js to start working on your app </Text>
	<StatusBar style="auto" />
</View>
);
}

const styles = StyleSheet.create({
	container: {
	flex: 1,
	backgroundColor: '#fff',
	alignItems: 'center',
	justifyContent: 'center'
	}
});
```
In your smartphone install `Expo Go` -> you can preview your Expo apps that are built on your local computer :
- open termianl `npm start` (it will start the Expo Dev Server and QR code > scan and open with Expo Go)


## Setting Up  a Local  Dev Environment
INSTALL `Android Studio`
- `More Actions` > `Vrtual Device Manager` > create virtual device (pixel 5 API 32) > play this virtual

`npm start` this process has to be running > `Press a | open Android` 












