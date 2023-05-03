[[_ 0 React Native Navigation]]

create a new file screen MealDetailScreen:
```jsx
import {View, Text, Pressable, Image, StyleSheet} from 'react-native';

const MealDetailScreen = (props) => {

    return(
        <Text> Some detailes </Text>
    );
}

export default MealDetailScreen;
```

register it in App.js:
```jsx
//...
     <Stack.Screen name="MealsOverview"
                   component={MealsOverviewScreen}/>
     <Stack.Screen name="MealDetail"
                   component={MealDetailScreen}/>
 
   </Stack.Navigator>
</NavigationContainer>
      //..
```

go to MealItem.jsx (of course you can make it in MealsOverviewScreen)
bu the first one is not registered so something new you have to do
Add  `import useNavigation`, `function selectMealItemHandler`, `onPress={selectMealItemHandler}`
```jsx
import {View, Text, Pressable, Image, StyleSheet} from 'react-native';
import { useNavigation } from '@react-navigation/native';

function MealItem(props){

    const navigation = useNavigation();

    function selectMealItemHandler(){
          //in the second param you can send some data
            navigation.navigate('MealDetail', {
            mealId: props.id
        })
    }

    return  <View style={styles.mealItem}>
            <Pressable android_ripple={{ color: '#ccc'}}
                       style={ ({pressed}) => (pressed ? styles.buttonPressed : null) }
                       onPress={selectMealItemHandler}
            > {/*style=... it is  for iOS */}
                <View>
//....
```
you have to add `id` property in `MealsOverViewScreen`
```jsx
//...
function renderMealItem(itemData){
        const mealItemProps = {
            id: itemData.item.id,
            title: itemData.item.title,
            imageUrl: itemData.item.imageUrl,
            affordability: itemData.item.affordability,
            complexity: itemData.item.complexity,
            duration: itemData.item.duration,
        }
        return  <MealItem {...mealItemProps}   />
    }
//..
```

because we use  `navigation.navigate('MealDetail', {mealId: props.id}`
we can use route
```jsx
import {View, Text, Pressable, Image, StyleSheet} from 'react-native';

const MealDetailScreen = (props) => {
    const mealId =props.route.params.mealId;
    return(
            <Text> Some detailes( { mealId }) </Text>
    );
}

export default MealDetailScreen;
```




