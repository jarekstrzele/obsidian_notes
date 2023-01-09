#react_native #monson-haefel_richard #plurasight 

---

# Intro React Native
allows to develop a single app in JavaScript for iOS and Android

Three important features in mobile apps:
1. navigation [[REACT NATIVE/plurasight/Building Mobile Apps with React Native/3 - React Native - Stack navigation]]
2. gestures [[REACT NATIVE/plurasight/Building Mobile Apps with React Native/4 - React Native - Gesture handlers]]
3. data exchange with Web APIs [[REACT NATIVE/plurasight/Building Mobile Apps with React Native/5 - React Native - XMLHttpRequest]]

##### React Native 3.27
##### Node.js 12.19
##### NPM

>[!a virtual device]
>software that imitates the behavior of a combination of hardware and operationg system
>are not perfect

##### ANDROID STUDIO EMULATOR:
- mobile app
- virtual operating system
- virtual device

## installing software
- https://nodejs.org/ (`node -v`)
- npm (`npm -v`)
- ==Expo== React Native development environment: `npm install --global expo-cli` (course "Building React Native Applications Using Expo ")

## first project
`expo init movie-time`

## Android Studio
remember about Android SDK
In WIndows we need to set the `ANDROID_HOME` and the `JAVA_HOME` envirenment variables

run Android > select 'No Activity'
==AVD== (Android Virtual Device) (in tools menu) > Phone >Pixel 3a >> Q (quick boot)
Startup orientation - Portrait; 
>[!important]
>To use this AVD with React Native it has to be running before you start a React application

Run Devices > in the folder with project (`expo init movie-time`) write 
#### `expo start`

>[!Metro Bundler]
> -  It is run by the Node.js server you installed earlier
> - It is a Expo GUI interface for running React Native applications

next press `a` open Android




























