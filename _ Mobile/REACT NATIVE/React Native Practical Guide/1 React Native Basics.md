[https://snack.expo.dev](https://snack.expo.dev)

[[_ 0 React Native - Practical Guide]]

	[[1.2. Handling Events]]
	[[1.3. Scrolling]]
	[[1.4. FlatList]]
	[[1.5. Splitting Components into Smaller Components]]
	[[1.6 Press to Delete and Style it]]
	[[1.7 Modal Screen]]
	

# Root component

App.js
```js
import {StyleSheet, Text, View } from 'react-native';

function App(){
  return (
    <View style={styles.container}>
	     <Text> Hello World!! </Text>
	     <Text> Witaj świecie </Text>
     </View>
  );

}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
});

export default App ;
```

There is some core components that are translate to native UI widget.
You use this them to buid your own UI

==There is no CSS !!==
To Style:
- `inline Styles`
- `StyleSheet Objects`
The syntax is similar to CSS

All other components have to be children/descendents of this app component


# Working with Core Components

## `<Text>`
String/text must be rendered within a `<Text>` component

## `<View>`
It generally build boxes and containers that hold other content.
It can contain:
- text,
- image, 
- button
- ....
- 
It is able to hold and layout some thing, but **it is not able** to **display** something


## `<Button />`
You have to import `Button`
`import {StyleSheet, Text, View, Button } from 'react-native';`

correctly: `<Button title="Click me!!" />`
wrong:  `<button> Click me </button>`

```js
function App(){
  return (
    <View style={style.container}>
     <Text> text </Text>
     <Button title="Click me!!" />
      <View>
        <Button title="Don't Click me!!" />
      </View>
    </View>
  );
}
```

# Styling React Native Apps
==There is no CSS!!==

> https://reactnative.dev/docs/style
> https://reactnative.dev/docs/colors

## Inline
## `style` props

`<Text style={ {margin:16, borderWidth: 2, borderColor: 'red', padding: 16} }>`


## StyleSheet Object
```js
import {StyleSheet, Text, View, Button } from 'react-native';

function App(){
  return (
    <View style={styles.container}>
     <Text style={styles.superText}> text </Text>
     <Button title="Click me!!" />
    <View>
     <Button  title="Don't Click me!!" />
    </View>
     <Text style={styles.superText}> New text </Text>

    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#ff0',
    alignItems: 'center',
    justifyContent: 'center',
  },

 superText: {
   margin:10,
   borderWidth: 3,
   borderColor: "red",
   padding:10,
   color: 'gray',
  },

});

export default App ;
```

# Layouts

```js
import {StyleSheet, Text, View, Button, TextInput } from 'react-native';

function App(){
  return (
    <View style={styles.appContainer}>
      <View >
      <TextInput placeholder="Your life goals!" />
      <Button title="Add a new goal" />
     </View>

     <View>
      <Text> List of your life goals ... </Text>
     </View>
    </View>

  );
}

const styles = StyleSheet.create({
 appContainer:{
   padding:50,
 }
});

export default App ;
```

## FLEXBOX 
Flexbox controls layouts in React Native!!

Two Axis:
- Cross Axis (left-right)
- Main Axis (top-bottom)

`flex: 1` the element (container) should expand to occupy available space
`flexDirection` controls the orientations of "Main Axis" and "Cross Axis"
`flexDirection: 'column'` -> elements are laid out in a column (Main Axis is from Top to Bottom)
`flexDirection: 'row'` -> elements are laid out in a row (MainAxis is from Left to Right)

`justifyContent: 'space-between'`  how the elements are laid out in their axis (e.g. space between them)

```js
import {StyleSheet, Text, View, Button, TextInput } from 'react-native';

function App(){
  return (
    <View style={styles.appContainer} >
      <View style={styles.inputContainer} >
        <TextInput style={styles.textInput} placeholder="Your life goals!" />
        <Button title="Add goal" />
      </View>
      <View>
        <Text> List of your life goals ... </Text>
      </View>
    </View>
  );

}

const styles = StyleSheet.create({
 appContainer:{
   padding:50,
 },
 inputContainer: {
   flexDirection: 'row' ,
   justifyContent: 'space-between'
 },
 textInput: {
   borderWidth: 1,
   borderColor: '#cccccc',
   width: '80%',
   marginRight: 8,
   padding: 8
 }

});

export default App ;
```


## DUMMY APP
```js
import React from 'react';
import {Text, View} from 'react-native';

const App = () => {
  return(
    <View style={ { padding: 50 } }>
      <View
        style={ {
          backgroundColor: 'red',
          width: 100,
          height: 100,
          justifyContent: 'center',
          alignItems: 'center'
        }}>
        <Text> 1</Text>
      </View>

       <View
        style={ {
          backgroundColor: 'blue',
          width: 100,
          height: 100,
          justifyContent: 'center',
          alignItems: 'center'
        }}>
        <Text> 2 </Text>
      </View>

       <View
        style={ {
          backgroundColor: 'green',
          width: 100,
          height: 100,
          justifyContent: 'center',
          alignItems: 'center'
        }}>
        <Text> 3 </Text>
      </View>
    </View>
  );
}

export default App ;
```


change
`<View style={ { padding: 50 } }>`
to
`<View style={ { padding: 50, flexDirection: 'row' } }>` ('column' by defalt)
or
`<View style={ { padding: 50, flexDirection: 'row-reverse' } }>`


### How a child element is sized?
In Dummy app each child element is `width:100`, `height:100` without these settings we will get very small squares 

You can set `width` and `height` in the parent box  (delete them from children)
```js
 <View style={ { padding: 50, flexDirection:'row', width:'80%', height:300 } }>

     <View

```

```js
<View style={ { padding: 50, flexDirection:'column', width:'80%', height:300 } }>

      <View

```


if `flexDirection: 'row'`  the **main axis** is from left to right
if `flexDirection: 'column'` (by default) the main axis is from top to bottom

`justifyContent` rules with the **main axis**
`alignItems` rules with the **cross axis** 
values:
- `center`
- `flex-end`
- `flex-start`
- `space-around`
- `space-between`
- `space-evenly`

*coś nie działa*:
by default `View` take as much space as their child elements require
but if you set up `flex:1` in the child elment, the child take as much space as it can

zmień padding głównego View na 10

```js
import React from 'react';
import {Text, View} from 'react-native';

const App = () => {
  return(
    <View style={ { padding: 10, flexDirection:'column', width:'80%', height:300, justifyContent: 'space-around',
        alignItems: 'strech' } }>
      <View
        style={ {
          backgroundColor: 'red',
          flex: 2,
          justifyContent: 'center',
          alignItems: 'center'
        }}>
        <Text> 1</Text>
      </View>

       <View
        style={ {
          backgroundColor: 'blue',
          flex: 3,
          justifyContent: 'center',
          alignItems: 'center'
        }}>
        <Text> 2 </Text>
      </View>

       <View
        style={ {
          backgroundColor: 'green',
          flex: 1,
          justifyContent: 'center',
          alignItems: 'center'
        }}>
        <Text> 3 </Text>
      </View>
    </View>
  );
}

export default App ;
```


## Improving layout
You work with that code:
```js
import {StyleSheet, Text, View, Button, TextInput } from 'react-native';

function App(){
  return (
    <View style={styles.appContainer} >
      <View style={styles.inputContainer} >
        <TextInput style={styles.textInput} placeholder="Your life goals!" />
        <Button title="Add goal" />
      </View>
      <View>
        <Text> List of your life goals ... </Text>
      </View>
    </View>
  );

}

const styles = StyleSheet.create({
 appContainer:{
   padding:50,
 },
 inputContainer: {
   flexDirection: 'row' ,
   justifyContent: 'space-between'
 },
 textInput: {
   borderWidth: 1,
   borderColor: '#cccccc',
   width: '80%',
   marginRight: 8,
   padding: 8
 }

});

export default App ;
```

change `appContainer: { padding:50 } ...` for `appContainer: { paddingTop: 50, paddingHorizontal: 16`

change
```js
 textInput: {
   borderWidth: 1,
   borderColor: '#cccccc',
   width: '70%' //width frin 80 to 70
```

>[!important] Button vs style
>Button has no `style` property

change:
```js
 inputContainer: {
   flexDirection: 'row' ,
   justifyContent: 'space-between',
   alignItems: 'center', // I added this line
   paddingBottom: 24 // I addeed this line
```

```js
const styles = StyleSheet.create({
 appContainer:{
  flex: 1,
  paddingTop:50,
  paddingHorizontal: 16
 },

 inputContainer: {
  flex:1,
  flexDirection: 'row' ,
  justifyContent: 'space-between',
  alignItems: 'center',
  marginBottom: 24,
  borderBottomWidth:1,
  borderBottomColor: '#cccccc'
 },

 textInput: {
   borderWidth: 1,
   borderColor: '#cccccc',
   width: '70%',
   marginRight: 8,
   padding: 8
 },

goalsContainer: {
  flex:5,
},
});

export default App ;
```


