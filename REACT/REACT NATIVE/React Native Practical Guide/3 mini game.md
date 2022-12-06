[[_ 0 React Native - Practical Guide]]



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

\
 













