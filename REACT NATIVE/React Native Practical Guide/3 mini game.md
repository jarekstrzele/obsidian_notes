[[REACT NATIVE/React Native Practical Guide/_ 0 React Native - Practical Guide]]

# Setting up our screen components


add new folders:
- `screen`, -> files 
	- StartGameScreen.jsx
	- GameScreen.jsx
	- GameOverScreen.jsx
- `components`

StartGameScreen.jsx
```jsx
import {TextInput, View , StyleSheet} from 'react-native' ;
import PrimaryButton from '../components/PrimaryButton.jsx' ;

function StartGameScreen() {

  return (
<View style={styles.inputContainer}>
  <TextInput style={styles.numberInput} maxLength={2}  
            keyboardType="number-pad"
            autoCapitalize="none" autoCorrect={false} />
  <PrimaryButton> Reset </PrimaryButton>
  <PrimaryButton> Confirm </PrimaryButton>
</View>
  );
}
  

export default StartGameScreen ;

const styles = StyleSheet.create({
  inputContainer: {
    //flex:1,
    marginTop: 100,
    padding: 10,
    marginHorizontal: 24,
    backgroundColor: '#72063c',
    borderRadius: 8,

    // css boxShadow
    elevation: 5, // android
     // shadowColor, shadowOffse(width: number, height: number), shadowOpacity{: 0.23}, shadowRadius(: number)
  },
  numberInput: {
    height: 50,
    width: 50,
    fontSize: 25,
    borderBottomColor: '#ddb52f',
    borderBottomWidth: 2,
    color: '#ddb52f',
    marginVertical: 8,
    fontWeight: 'bold',
    textAlign: 'center'
  }

}) ;
```

PrimaryButton.jsx
```jsx
import {View, Text} from 'react-native' ;

const PrimaryButton = (props) => {
  return (
    <View>
    <Text> {props.children} </Text>
    </View>
  )
}

export default PrimaryButton ;
```



## PrimaryButton -> pressable and styling
```jsx
import {View, Text, Pressable} from 'react-native' ;

const PrimaryButton = (props) => {
  function pressHandler(){
    console.log('Pressed!')
  }

  return (
  <Pressable onPress={pressHandler}>
    <View>
      <Text> {props.children} </Text>
    </View>
  </Pressable>
  )
}

export default PrimaryButton ;
```

#### styling button


```jsx
import {View, Text, Pressable, StyleSheet} from 'react-native' ;

const PrimaryButton = (props) => {
  function pressHandler(){
    console.log('Pressed!')
  }

  return (
   <View style={styles.btnContainer} android_ripple={{color:'dark'}}>
      <Pressable onPress={pressHandler} >
          <Text style={styles.btnText}> {props.children} </Text>  
      </Pressable>  
  </View>
  )
}

export default PrimaryButton ;
  

const styles = StyleSheet.create({
  btnContainer:{
    backgroundColor: '#25979c',
    borderRadius: 28,
    paddingVertical: 8,
    paddingHorizontal: 16,
    elevation: 2,
    margin: 4,
  },

  btnText:{
    color:'white',
    textAlign: 'center'
  }

});
```

to ripple effect inside:
- change `View` with `Pressable` (like above)
- and make two container styles

```jsx
return (

   <View style={styles.btnOuterContainer} >

      <Pressable 
	      style={styles.btnInnerContainer} 
	      onPress={pressHandler} 
	      android_ripple={{color:'dark'}}>

          <Text style={styles.btnText}> {props.children} </Text>  

      </Pressable>  

  </View>

  )
 
const styles = StyleSheet.create({
  btnOuterContainer:{
    borderRadius: 28,
    margin: 4,
    overflow: 'hidden'
  },
  btnInnerContainer:{
    backgroundColor: '#25979c',
    paddingVertical: 8,
    paddingHorizontal: 16,
    elevation: 2,
  },
  btnText:{
    color:'white',
    textAlign: 'center'
  }
});
```


##### for iOS you have to add another style

```jsx
  return (
   <View style={styles.btnOuterContainer} >
      <Pressable
        style={(pressed) =>
          pressed
            ? [styles.btnInnerContainer, styles.pressed]
            : styles.btnInnerContainer
          }
        onPress={pressHandler}
        android_ripple={{color:'dark'}}
      >
          <Text style={styles.btnText}> {props.children} </Text>  
      </Pressable>  
  </View>
  )
}
 btnText:{
    color:'white',
    textAlign: 'center'
  },
  pressed:{
    opacity: 0.75,
  }
});
```


#### imporoving btns

in StartGameScreem
```jsx
const styles = StyleSheet.create({

  inputContainer: {
    justifyContent: 'center',
    alignItems: 'center',
```

other changes
to position buts next to each other you have to wrap them into seperated `View`

```jsx
  return (
<View style={styles.inputContainer}>
  <TextInput style={styles.numberInput} maxLength={2}  
            keyboardType="number-pad"
            autoCapitalize="none" autoCorrect={false} />
  <View>
    <PrimaryButton> Reset </PrimaryButton>
    <PrimaryButton> Confirm </PrimaryButton>
  </View>
</View>
  );
}

export default StartGameScreen ;

const styles = StyleSheet.create({
  inputContainer: {
    justifyContent: 'center',
    alignItems: 'center',
    marginTop: 100,
    padding: 10,
    marginHorizontal: 24,
```


another change
add  to Style
```jsx
<View style={styles.btnsContainer}>
    <PrimaryButton> Reset </PrimaryButton>
    <PrimaryButton> Confirm </PrimaryButton>
  </View>
...
btnsContainer:{
    flexDirection: 'row'
  }
```

to make button equal width:
```jsx
<View>
     <PrimaryButton> Reset </PrimaryButton>
   </View>
   <View>
     <PrimaryButton> Confirm </PrimaryButton>
   </View>
```

==StartGameScreen==
```jsx
import {TextInput, View , StyleSheet} from 'react-native' ;
import PrimaryButton from '../components/PrimaryButton.jsx' ;

function StartGameScreen() {

  return (
<View style={styles.inputContainer}>
  <TextInput style={styles.numberInput} maxLength={2}  
            keyboardType="number-pad"
            autoCapitalize="none"
            autoCorrect={false}
   />
  <View style={styles.btnsContainer}>
      <View style={styles.btnContainer}>
        <PrimaryButton> Reset </PrimaryButton>
        <PrimaryButton> Confirm </PrimaryButton>
     </View>
  </View>
</View>
  );
}

export default StartGameScreen ;
```


--------------------
# Background Coloring

`<View>` takes only space that is needed ==!!!!!!==
`flex:1` take a many space that is possible
App.jsx
```jsx
import { StyleSheet, Text, View, StatusBar } from 'react-native';
import StartGameScreen from './screens/StartGameScreen.jsx' ;

export default function App() {
return (
<View style={styles.mainContainer}>
<StartGameScreen />
</View>
);
}

const styles = StyleSheet.create({
mainContainer:{
	flex: 1,
	backgroundColor: '#f8e7ff',
}
});
```
if you set up a backgrund color in the App, the same color will be in other screens


## Linear Gradiant
inside the project folder (maybe)
### `expo install expo-linear-gradient`

and than you can import `{LinearGradient}`
App.jsx
```jsx
import { StyleSheet,View, Text } from 'react-native';
import StartScreen from './screens/StartScreen.jsx' ;
import { LinearGradient } from 'expo-linear-gradient' ;

export default function App() {
  return (
    <LinearGradient colors={['#f8e7ff','#2bb1b7' ]} style={styles.mainContainer}>
      <StartScreen />
    </LinearGradient>
  );
}
  
const styles = StyleSheet.create({
  mainContainer:{
    flex: 1,
    backgroundColor: '#f8e7ff'
  }
});
```


## Adding a Background image
You have to use `ImageBackground`  buit-in component!
https://unsplash.com

```jsx
//..
export default function App() {
  return (
    <LinearGradient colors={['#f8e7ff','#2bb1b7' ]} style={styles.mainContainer}>
	      <ImageBackground source={require('./assets/dices-unsplash.jpg')}          resize="cover" 
	                       style={styles.mainContainer}>
      <StartScreen />
        </ImageBackground>
    </LinearGradient>
  );
}
```

resizeMode: 
	- cover
	- strech
	- ...
- 

Gradient is disapeared, but if you delete `backgroundColor:...` from `mainContainer` you obtain a background image and gradiant
App.js
```js
import { StyleSheet, ImageBackground } from 'react-native';
import StartScreen from './screens/StartScreen.jsx' ;
import { LinearGradient } from 'expo-linear-gradient' ;

export default function App() {
  return (
    <LinearGradient colors={['#111aa7', '#18eFff' ]} style={styles.mainContainer}>
      <ImageBackground source={require('./assets/dices-unsplash.jpg')}
                       resizeMode="strech"
                       style={styles.mainContainer}
                       imageStyle={styles.backgroundIMG}>
          <StartScreen />
        </ImageBackground>
    </LinearGradient>
  );
}

const styles = StyleSheet.create({
  mainContainer:{
    flex: 1,
    },
    backgroundIMG:{
      opacity: 0.2
    }
});
```

## Game logic

in App.js add:
- `const [enteredNumber, setEnteredNumber] = useState('');`
- function `numberInputHandler`, `confirmInputHandler`
- in `TextInput` `value={enteredNumber}`
- in `PrimaryButton` a new attribute `onPress={confirmInputHandler}`
```jsx
  

import {TextInput, View , StyleSheet} from 'react-native' ;
import PrimaryButton from '../components/PrimaryButton.jsx' ;
import { useState } from 'react' ;

function StartScreen() {
  const [enteredNumber, setEnteredNumber] = useState('');

  function numberInputHandler(enteredText){
    setEnteredNumber(enteredText) ;
  }

  function confirmInputHandler(){
  }

  return (
<View style={styles.inputContainer}>
  <TextInput  style={styles.numberInput}
             maxLength={2}  
             keyboardType="number-pad"
             autoCapitalize="none"
             autoCorrect={false}
             onChangeText={numberInputHandler}
             value={enteredNumber}
   />
  <View style={styles.btnsContainer}>
     <View style={styles.btnContainer}>
        <PrimaryButton> Reset </PrimaryButton>
        <PrimaryButton onPress={confirmInputHandler}> Confirm </PrimaryButton>
     </View>
  </View>
</View>
  );
}

export default StartScreen ;
 

const styles = StyleSheet.create({
    inputContainer: {
      alignItems: 'center',
      marginTop: 100,
      padding: 10,
      marginHorizontal: 24,
      backgroundColor: '#2aa1b7',
      borderRadius: 8,
      // css boxShadow
      elevation: 5, // android
       // shadowColor, shadowOffse(width: number, height: number), shadowOpacity{: 0.23}, shadowRadius(: number)
    },
    numberInput: {
      height: 50,
      width: 50,
      fontSize: 25,
      borderBottomColor: '#f8e7ff',
      borderBottomWidth: 2,
      color: '#f8e7ff',
      marginVertical: 8,
      fontWeight: 'bold',
      textAlign: 'center'
    },

    btnsContainer:{
      flexDirection: 'row'
    },
    btnContainer:{
      flex:1
    }
  }) ;
```

in PrimaryButton.js add
- change `props` into `{children, onPress} =>`
- in `Pressable` attribute `onPress={onPress}`
```jsx
import {View, Text, Pressable, StyleSheet} from 'react-native' ;

const PrimaryButton = ({children, onPress }) => {
  return (
   <View style={styles.btnOuterContainer} >
      <Pressable
        style={(pressed) =>
          pressed
            ? [styles.btnInnerContainer, styles.pressed]
            : styles.btnInnerContainer
          }
        onPress={onPress}
        android_ripple={{color:'white'}}
      >
         <Text style={styles.btnText}> {children} </Text>  
     </Pressable>  
  </View>
  )
}

  export default PrimaryButton ;


const styles = StyleSheet.create({
  btnOuterContainer:{
    borderRadius: 28,
    margin: 4,
    overflow: 'hidden'
  },

  btnInnerContainer:{
    backgroundColor: '#25979c',
    paddingVertical: 8,
    paddingHorizontal: 16,
    elevation: 2,
  },

  btnText:{
    color:'white',
    textAlign: 'center'

  },

  pressed:{
    opacity: 0.75,
  }
});
```




















