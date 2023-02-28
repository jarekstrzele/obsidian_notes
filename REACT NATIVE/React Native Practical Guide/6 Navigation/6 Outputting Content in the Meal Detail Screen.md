[[_ 0 React Native Navigation]]

create a new component `MealDetails.jsx` (cut some code from MealItem )
```jsx
import {View, Text, StyleSheet} from 'react-native';

function MealDetails(props){

	return (
        <View style={styles.details}>
            <Text style={styles.detailItem}>{props.duration}  </Text>
            <Text style={styles.detailItem}>{props.complexity.toUpperCase()}  </Text>
            <Text style={styles.detailItem}>{props.affordability.toUpperCase()}  </Text>
        </View>
    )
}

export default MealDetails;

const styles = StyleSheet.create({
    details:
    {
        flexDirection: 'row',
        alignItems: 'center',
        justifyContent: 'center',
        padding: 8
    },
    detailItem:{
        marginHorizontal: 4,
        fontSize: 12
    },
})
```

Now you can use that component in MealItem
```jsx
//..
<Image source={{uri: props.imageUrl}} style={styles.image}/>
      <Text style={styles.title}> {props.title} </Text>
     </View>

	<MealDetails duration={props.duration}
                 affordability={props.affordability}
                 complexity={props.complexity}/>

 </Pressable>
//....
```

SOME CHANGES IN MEAL DETAIL SCREEN
```jsx
import {View, Text, Image, StyleSheet} from 'react-native';
import MealDetails from '../components/MealDetails';
import { MEALS } from '../data/dummy-data';

const MealDetailScreen = (props) => {
    const mealId =props.route.params.mealId;
    const selectedMeal = MEALS.find((meal)=>meal.id === mealId);

return(
    <View>
        <Image source={ {uri: selectedMeal.imageUrl} } />
        <Text> {selectedMeal.title} </Text>
        <MealDetails duration={selectedMeal.duration}
                     complexity={selectedMeal.complexity}
                     affordability={selectedMeal.affordability}
        />
        <View>
        </View>
        <Text>Ingredients</Text>
        {selectedMeal.ingredients.map((ingredient) => (<Text key={ingredient}> {ingredient} </Text>))}
        <Text>Setps</Text>
        {selectedMeal.steps.map((step) => (<Text key={step}> {step} </Text>))}
    </View>
    );
}

export default MealDetailScreen;
```

Cascading style by `[ ]` merging styles
got o `MealDetails`
```jsx
function MealDetails(props){

 return (
   <View style={[ styles.details, props.style ]}>
       <Text style={[ styles.detailItem, props.textStyle]}>{props.duration}  </Text>
       <Text style={[ styles.detailItem, props.textStyle]}>{props.complexity.toUpperCase()}  </Text>
       <Text style={[ styles.detailItem, props.textStyle]}>{props.affordability.toUpperCase()}  </Text>
  </View>
    )
```

you have to add this special `text style` in the `MealFetailScreen`
```jsx

```













