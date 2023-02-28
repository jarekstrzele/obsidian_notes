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











