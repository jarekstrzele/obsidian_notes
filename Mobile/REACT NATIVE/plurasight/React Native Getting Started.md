#plurasight  #react_native  #dawson_reggie

---
# React Native Getting Started

Version:
- React Native 0.63.4
- React 16.13.1

## Why choose React Native
- one codebase for all platform
- renders to Native (JavaScript renders to native code)
- Preview the app (View changes to the app without build)
- use standard JS
- eay to learn
- releasing a React Native App:
	- Build the app and release to the app stores
	- PWA/Desktop apps (create Progressing Web Apps and Desktop apps)

## React Native Basics
- when we build React Native apps we are using components as the building blocks
```javascript
const MyButton = () => {
	return (
		<Text> Press Me!</Text>
	);
}
```
- as we compose our own components in our app, we will use [[JSX]]
- PROPERTIES `props` are used (props are IMMUTABLE):
```javascript
const CurrentUser = (props) => {
	return (
		<Text> {props.username} is loggedin </Text>
	)
}

const Users = () => {

	return (
		<View>
			<CurrentUser username="John" />
		</View>
	)
}

```

- if we want to manage mutable data, we use STATE:
```javascript
const NewBook = () => {
	const [theBook, setBook] = useState(bookData);
	return (
		<View>
			<Text>
				{theBook} is out now, get you copy!
			</Text>
		</View>
	);

}
```

- React Navigation (to navigate between different screens)
	- it allows you to create routes that translate to the individual views that make up your app
```javascript
const Stack = createStackNavigator();
const MyStack = () => {
	return (
		<NavigationContainer>
			<Stack.Navigator>
				<Stack.Screen name="Home" component={HomePage} />
			</Stack.Navigator>
		</NavigationContainer>
	);
}
```

----------------------------
# Setting up React Native
- Node
- OpenJDK (https://openjdk.org/) (https://www.linuxcapable.com/how-to-install-openjdk-18-on-ubuntu-22-04-lts/)
- Android Studio:
	- configure > SDK Manager 
		- > System Settings select Android SDK, (Android 11.0 R) Google Play System Image
		- > SDK Tools
			- > select Andoid SDK Build-Tools
			- >Android Emulator (Hypervisor)(for AMD processor) or Intel Emulator Accelerator (HAXM)
- add some environment variables
	- Windows use System Properies panel > click on environment variables> click on new: Variable name ANDROID_HOME, value is path from Android Studio
- Linux add to your `$HOME/.bash_profile` or `$HOME/.bashrc`:
```bash
export ANDROID_HOME=$HOME/Library/Android/sdk
export PATH=$PATH:$Android_HOME/emulator
export PATH=$PATH:$Android_HOME/tools
export PATH=$PATH:$Android_HOME/tools/bin
export PATH=$PATH:$Android_HOME/platform-tools
```

## Creating an App
`npx` allows you to use Node packages without installing them

`--version` Use a specific version of React Native
`--template` Use a specific template for the app generated
`--directory` create a custom directory for the project

#### `npx react-native init GloboTicket`
where `GloboTicket` is the name of app and the folder with this name will be created

Now go to Android Studio (Configure tab and choose AVD Manager-Virtual (Virtual Device Manager) > if there are now virtual device, we need to create it).

Now in the app folder:
#### `npx react-native start` 
This will start Metro, which will bundle your app and start a dev server. 
or
This is unnecessary step, because instead you can launch your Adroid emulator (Virtual Devices). The emulator i treated like an actual device that is connected to your computer
#### or
you can use 
#### `npx react-native run-android`

Na Windowsie wszystko działa
BUT I HAVE PROBLEMS to start this app:
I did:
- a new project `expo init appName`
- started a Android Studio Emulator 
- `expo start`
- (I had to `npm install react-native-screens`)


---
# Creating Your first Component

## Class based components
```javascript
import React, { Component } from 'react';

class Home extends Component{
    render(){
        return (...);
    }
}

export default Home;
```


## Functional components
`props` (properties) is a way for developers to set these properties when the component is created. ==This props cannot be changed during the life of the component==. (for example: use props to set the border color of the component)
`state` data that could change or data from a remote source

With function components we don't need to use the render method!!!
```javascript
import React from 'react';

const Home = (props) => {
    return();
}

export default Home;
```


## Using the View Component
https://reactnative.dev/docs/view

>[!View]
The most fundamental component for building a UI, View is a container that supports layout with flexbox, style, some touch handling, and accessibility controls. View maps directly to the native view equivalent on whatever platform React Native is running on, whether that is a UIView, android.view, etc.

## Image component
>[!image]
>A React component for displaying different types of images, including network images, static resources, temporary local images, and images from local disk, such as the camera roll.


## Text Component
>[!text]
>A React component for displaying text.
>Text supports nesting, styling, and touch handling.


## Applying styles to components
root > `react-native.config.js:`
```javascript
module.exports = {
    project: {
        ios: {},
        android: {},
    },
    assets: ['./assets/fonts'],
};
// in this folder I copy Google Ubuntu fonts
```
`npx react-native link` this command will copy the fonts to our Android project for us


## Viewing the Component







----
# Routing Between COmponents












---------------

# Creating a Form Component














-------
# Retrieving Remote Data using the Fetch API






-------
# Generationg a Build of the App



























