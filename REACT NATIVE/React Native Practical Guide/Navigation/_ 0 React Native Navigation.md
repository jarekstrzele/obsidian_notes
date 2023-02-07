
>[!info] Navigation
> 



```
npx create-expo-app FirstNavig
cd AwesomeProject  
npx expo start
```

# First nav app with dishes
new folders: 
- component
	- CategoryGridTitle.jsx
- data
	- dummy-data.js (Obisidian doesm't see it)
- models
	- category.js  (Obisidian doesm't see it)
	- meal.js  (Obisidian doesm't see it)
	- 
- screens
	- CategoriesScreen.jsx

`CategoriesScreen.jsx`
[[1.4. FlatList]]
```jsx
import { FlatList } from "react-native";
import CategoryGridTitle from "../components/CategoryGridTitle";
import { CATEGORIES } from "../data/dummy-data";

const renderCategoryItem = (itemData) => {
    return <CategoryGridTitle title={itemData.item.title}
                              color={itemData.item.color} />;
}
  

function CategoriesScreen(){
    return <FlatList data={CATEGORIES}
                     keyExtractor={(item)=> item.id}
                     renderItem={renderCategoryItem} />
}

export default CategoriesScreen
```


`CategoryGridTitle.jsx`
```jsx
import {Pressable, View, Text } from 'react-native';
const CategoryGridTitle = ({title, color}) => {
        return <View>
                <Pressable>
                    <View>
                        <Text>
                            {title}
                        </Text>
                    </View>
                </Pressable>
              </View>
}
export default CategoryGridTitle;
```


`App.jsx`
```jsx
import { StyleSheet, Text, View } from 'react-native';
import CategoriesScreen from './screens/CategoriesScreen';


export default function App() {
  return (
    <CategoriesScreen />
  );
}
const styles = StyleSheet.create({
  container: {
  },
});
```


# Some styling
to change background color in all app:
- go ro `app.json`
- `expo`> add `backgroundColor: new value`
- reload







