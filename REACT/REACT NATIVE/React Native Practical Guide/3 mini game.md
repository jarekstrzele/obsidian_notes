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
            autoCapitalize="none" autoComplete={false} />
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

PrimaryButton -> pressable and styling
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


