#react_native  #plurasight  #reactavichandran_adhithi 

---
# React Native - The Big Picture
[[REACT NATIVE/REACT NATIVE/plurasight/React Native - The Big Picture 1]]



---
# What is React Native RN

>[!RN]
>It is a UI framework that let you use JS and RN to build a native mobile app:
>Native iOS and Android App

RN comes from FaceBook 2015

### Prerequisites:
- Javascript
- React
- JSX
- thinking like a mobile developer

### Styleing in React Native
- no CSS or special language
- use JS for styling
- style name and  values match CSS
- ecerything is defined in camel-case
- use FlexBox for layout
- each component can have its own corresponding stylesheet
- Platform-specific styling available for iOS and Android


## History
- 2013 Facebook -> React as a JS library for the web
- 2015 React Native as a mobile solution for building native apps using React
- 

## React Native Components
**component** represents small pieces of code that are organized together (like building blocks with its own functionality or UI)

1. **core components** come out of the box with React Native (when you installed RN, you have all these components)
	1. view, text, images, ScrollView ...
	2. They translates into the native iOS and native Android views
2. **Community Components** (for camera, Video, Audio, FingerPrints,  ....)
3. **your own native components**

>
>==RN Components are subset of React Components==
>
## Compose First RN Component
```javascript
import React from 'react';
import { Text, View } from 'react-native';

const HelloWordApp = () => {
	return {
		<View stryle= {{
			flex: 1,
			justifyContent: 'center',
			alignItems: 'center'
		}}>
		<Text>Hello, I am your first RN Component! </Text>
		</View>
	};
}

export defaul HelloWorldApp
```
THis i a simple React functional component. This function returns som JSX 

--------------------
# 3 Why React Native

- you know JS, RN is easy to learn
- 2020 web frameworks: the first is React.js
	- everything in React is a component - **Component-based architecture** where each unit of code is a component
	- the components allow us to reuse them across the code base
	- support one directional data flow (from parent to child)
	- flexibility (picking and choosing packages for our project)
	- easy to test
	- code sharing between wen and mobile (RN Web)
- cross-platform you build areal native mobile app
- superior developer experience:
	- hot reloading
	* debugger (React Inspector, Redux Dev tools)
	* over the air (OTA) updates (CodePush)
* cost effective
* excellent community https://reactnative.dev/

----------------
# 4 React Native Ecosystem
## expo
To start use `expo`
`npm install -g expo-cli`
next
`expo init myNewProject` -> this creates a new folder, so navigate to it and run project `npm start` (no Xcode or Android Studio)

expo provides access to:
- file system 
- camera
- location
- push notification
- native graphics
- push OTA Updates
- ...
IGNITE
- boilerplate kith with best practices built-in
- pattern library
- api testing
- themes

## Testing
"Quality means doing it right even when no ine is looking" (Henry Ford)

### Jest - Unit Tests
-      written in JS
	- works out of the box
	- powerful mocking library
	- build-in code coverage report
	- runs onluy test files related to changed files
	- support snapshot testing


### Detox - end to end testing
It runs your app on an actual device/ emulator and interacts with it just like a real user would


## Push notification
a puch notification is a message that pops up on a mobile device. Users don't have to be in the app or using their devices to receive them
#push_notification

- promoting products to increase sale
- sending time-sensitive notification
- ....

In `expo` it is build-in (see also `one single` or `Firebase cloud messaging` or `AWS Amplify`)


## Third Party Libraries
github 
	react-native-community
	react-

- `React Native Camera` 
- `React Native Fingerprint Scanner` or `React Native Touch ID`
- `react-native-video`
- `Reactr Navigation` (from screen to screen)
- 

## Deployments
- Over The Air Updates (OTA) using CODEPUSH
- Native Upades using FASTLANE
- TestFlight for iOS
- Crashlytics for Android 



