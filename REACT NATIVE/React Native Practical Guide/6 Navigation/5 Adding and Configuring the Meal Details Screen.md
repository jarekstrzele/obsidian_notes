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
bu the first one is not registered so someithing new you have to do
```jsx


```



