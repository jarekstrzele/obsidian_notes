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
       <MealDetails duration={selectedMeal.duration}
                     complexity={selectedMeal.complexity}
                     affordability={selectedMeal.affordability}
                     textStyle={styles.detailText}
//...
  

const styles = StyleSheet.create({
    mainView:{
        backgroundColor: '#880e4f'
    },
    image: {        
        width: '100%',
        height: 350,
        marginVertical:10,
        marginHorizontal: 10,
        borderRadius: 10
     },

    title: {
     fontWeight: 'bold',
     fontSize: 24,
     margin: 8,
     textAlign: 'center',
     color: '#ffebee',
    },
    detailText: {
        color: 'white'
    }
```


MEALDETAILSCEEN.jsx
```jsx
import {View, Text, Image, StyleSheet} from 'react-native';
import MealDetails from '../components/MealDetails';
import { MEALS } from '../data/dummy-data';

const MealDetailScreen = (props) => {
    const mealId =props.route.params.mealId;
    const selectedMeal = MEALS.find((meal)=>meal.id === mealId);
    return(
    <View style={styles.mainView}>
        <Image source={ {uri: selectedMeal.imageUrl}} style={ styles.image}  />
        <Text style={styles.title}> {selectedMeal.title} </Text>
        <MealDetails duration={selectedMeal.duration}
                     complexity={selectedMeal.complexity}
                     affordability={selectedMeal.affordability}
                     textStyle={styles.detailText}
        />

        <View style={styles.subtitleContainer}>
            <Text style={styles.subtitle}>Ingredients</Text>
        </View>
                {selectedMeal.ingredients.map((ingredient) => (<Text key={ingredient}> {ingredient} </Text>))}
        <View style={styles.subtitleContainer}>
            <Text  style={styles.subtitle}>Setps</Text>
        </View>
            {selectedMeal.steps.map((step) => (<Text key={step}> {step} </Text>))}
    </View>
    );
}


export default MealDetailScreen;

const styles = StyleSheet.create({
    mainView:{
          backgroundColor: '#880e4f'
    },
    image: {        
        width: '100%',
        height: 350,
        marginVertical:10,
        marginHorizontal: 10,
        borderRadius: 10,
     },
    title: {
     fontWeight: 'bold',
     fontSize: 24,
     margin: 8,
     textAlign: 'center',
     color: '#ffebee',
    },

    detailText: {
        color: 'white'
    },

    subtitle: {
        color: '#ffebee',
        fontSize: 18,
        fontWeight: 'bold',
        textAlign: 'center',
    },

    subtitleContainer:{
        borderBottomColor: 'white',
        borderBottomWidth: 2,
        padding: 6,
        marginHorizontal: 20,
        marginBottom: 10
    }

})
```


-------
#  new components
cut come code from MealDetailsSceen.jsx

## `Subtitle.jsx`
```jsx
import {View, Text, StyleSheet} from 'react-native';

function Subtitle(props){
	return (
        <View style={styles.subtitleContainer}>
            <Text  style={styles.subtitle}>{props.children}</Text>
        </View>
    );
}

export default Subtitle;

const styles = StyleSheet.create({
    subtitle: {
        color: '#ffebee',
        fontSize: 18,
        fontWeight: 'bold',
        textAlign: 'center',
    },
    subtitleContainer:{
        borderBottomColor: 'white',
        borderBottomWidth: 2,
        padding: 6,
        marginHorizontal: 20,
        marginBottom: 10
    }
})
```
use this component in `MealDetailSceen.jsx` with *ingredients* and *steps*.


## `List.jsx`
```jsx
import {View, Text, StyleSheet} from 'react-native';

function List(props){

    return (
        props.data.map((dataPoint) => (
            <View  key={dataPoint} style={styles.listItem}>
                <Text style={styles.itemText}> {dataPoint} </Text>
            </View>
            )
    ))
}


export default List;

const styles = StyleSheet.create({
    listItem: {
        borderRadius:6,
        paddingHorizontal: 8,
        paddingVertical: 4,
        marginVertical: 4,
        marginHorizontal: 12,
        backgroundColor: '#ffebee'

    },
    itemText:{
        color: '#880e4f',
        textAlign: 'center'
    }

});
```


MealDetailScee.jsx
```jsx
import {View, Text, Image, StyleSheet, ScrollView} from 'react-native';

import List from '../components/List';

import MealDetails from '../components/MealDetails';

import Subtitle from '../components/Subtitle';

import { MEALS } from '../data/dummy-data';

  
  

const MealDetailScreen = (props) => {

    const mealId =props.route.params.mealId;

    const selectedMeal = MEALS.find((meal)=>meal.id === mealId);

    return(

    <ScrollView style={styles.mainView}>

        <Image source={ {uri: selectedMeal.imageUrl}} style={ styles.image}  />

        <Text style={styles.title}> {selectedMeal.title} </Text>

        <MealDetails duration={selectedMeal.duration}

                     complexity={selectedMeal.complexity}

                     affordability={selectedMeal.affordability}

                     textStyle={styles.detailText}

  

        />

        <View style={styles.listOuterContainer}> {/* to make center*/}

            <View style={styles.listContainer}>      

                <Subtitle>Ingredients</Subtitle>

                <List data={selectedMeal.ingredients} />

                <Subtitle>Steps</Subtitle>

                <List data={selectedMeal.steps} />

            </View>

        </View>

  

    </ScrollView>

    );

}

  

export default MealDetailScreen;

  

const styles = StyleSheet.create({

    mainView:{

  

        backgroundColor: '#880e4f',

        marginBottom: 32,

    },

    image: {        

        width: '100%',

        height: 350,

        marginVertical:10,

        marginHorizontal: 10,

        borderRadius: 10,

     },

    title: {

     fontWeight: 'bold',

     fontSize: 24,

     margin: 8,

     textAlign: 'center',

     color: '#ffebee',

    },

    detailText: {

        color: 'white'

    },

    listContainer: {

        width: '80%'

    },

  

    listOuterContainer:{

        alignItems: 'center'

    }

  
  

})
```




