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


