add a new component MealItem in the components folder

Mealitem.jsx
```jsx
import {View, Text} from 'react-native';

function MealItem(props){
    return  <View>
                <Text> {props.title} </Text>
            </View>
}
export default MealItem;
```

some changes in `MealsOverviewscreen.jsx` add MealItem to this file
```jsx
import { View, FlatList, StyleSheet } from "react-native";
import { MEALS } from "../data/dummy-data";
import MealItem from "../components/MealItem";

function MealsOverviewScreen(props){

 const catId = props.route.params.categoryId;
 const displayedMeals = MEALS.filter((mealItem) => {
    return mealItem.categoryIds.indexOf(catId) >= 0;
 });


function renderMealItem(itemData){
    return  <MealItem title={itemData.item.title} />
}

    return(
        <View style={styles.container}>
            <FlatList data={displayedMeals}
                      keyExtractor={(item) => item.id}
                      renderItem={renderMealItem}
            />
        </View>
    )
}
```

styling MeatItem
```jsx
import {View, Text, Pressable, Image, StyleSheet} from 'react-native';
function MealItem(props){

    return  <View style={styles.mealItem}>
            <Pressable android_ripple={{ color: '#ccc'}}
                       style={ ({pressed}) => (pressed ? styles.buttonPressed : null) }
            > {/*style=... it is  for iOS */}
                <View>

                <Image source={{uri: props.imageUrl}} style={styles.image}/>
                <Text style={styles.title}> {props.title} </Text>
                </View>
                <View style={styles.details}>
                    <Text style={styles.detailItem}>{props.duration} m  </Text>
                    <Text style={styles.detailItem}>{props.complexity.toUpperCase()}  </Text>
                    <Text style={styles.detailItem}>{props.affordability.toUpperCase()}  </Text>
                </View>
            </Pressable>
            </View>
}

export default MealItem;
// a local file  jpg -> RN can display it without problems
// a remote file jpg -> you have to style height and width to display the image

const styles = StyleSheet.create({
    image:{
    width: '100%',
    height: 200
    },
    title:{
        fontWeight: 'bold',
        textAlign: 'center',
        fontSize: 18,
        padding:8
    },
    mealItem:{
        margin: 16,
        borderRadius: 8,
        overflow: 'hidden',
        backgroundColor: 'white',
        elevation: 4, //shadow for Android
        // shadow for iOS
        shadowColor: 'black',
        shadowOpacity: 0.25,
        shadowOffset: { width: 0, height: 2},
        shadowRadius: 8,
    },
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
    button: {
        flex: 1,
    },
    buttonPressed: {
        opacity: 0.5,
    }
})

```

> Ten styl to ustawienie wartości właściwości `overflow` w zależności od systemu operacyjnego, na którym działa aplikacja React Native.
> 
> Jeśli systemem operacyjnym jest Android, wartość `overflow` ustawiana jest na `'hidden'`. Oznacza to, że treść, która przekracza rozmiar kontenera, zostanie ukryta.
> 
> Jeśli systemem operacyjnym nie jest Android, wartość `overflow` ustawiana jest na `'visible'`. Oznacza to, że treść, która przekracza rozmiar kontenera, będzie widoczna poza granicami kontenera.
> 
> Taka konstrukcja stylu może być przydatna, aby zapewnić spójny wygląd interfejsu użytkownika na różnych systemach operacyjnych. Dzięki temu można dostosować sposób wyświetlania treści w kontenerach w zależności od preferencji i wymagań systemu operacyjnego.


MealOverviewScreen
```jsx
import { View, FlatList, StyleSheet } from "react-native";
import { MEALS } from "../data/dummy-data";
import MealItem from "../components/MealItem";

function MealsOverviewScreen(props){

 const catId = props.route.params.categoryId;
 const displayedMeals = MEALS.filter((mealItem) => {
    return mealItem.categoryIds.indexOf(catId) >= 0;
 });

function renderMealItem(itemData){
    const mealItemProps = {
        title: itemData.item.title,
        imageUrl: itemData.item.imageUrl,
        affordability: itemData.item.affordability,
        complexity: itemData.item.complexity,
        duration: itemData.item.duration
    }
    return  <MealItem {...mealItemProps}   />
}

    return(
        <View style={styles.container}>
            <FlatList data={displayedMeals}
                      keyExtractor={(item) => item.id}
                      renderItem={renderMealItem}
            />
        </View>
    )
}

export default MealsOverviewScreen ;

const styles = StyleSheet.create({
    container: {
        flex:1,
        padding: 16 ,
    }

})


```












