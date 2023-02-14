[[_ 0 React Native Navigation]]

The  title in the screen comes from `name` attribute (it is a default header)
```jsx
<Stack.Screen name="MealsCategories"
              component={CategoriesScreen} />
```
https://reactnavigation.org/docs/native-stack-navigator#options

add `options={ { } }`

for one screen
```jsx 

export default function App() {
  return (
    <>
      <StatusBar style="dark" />
      <NavigationContainer>
        <Stack.Navigator>
          <Stack.Screen name="MealsCategories"
                        component={CategoriesScreen}
                        options={{
                          title:'All Categories',
                          headerStyle: { backgroundColor: "#991410" },
                          headerTintColor: "white",
                          contentStyle: { backgroundColor: '#3f2f'}
                           }
                          }
                        />
          <Stack.Screen name="MealsOverview"
                        component={MealsOverviewScreen}
                        />
        </Stack.Navigator>
      </NavigationContainer>
    </>
   );
}
```

for all screens
```jsx
  
export default function App() {
  return (
    <>

      <StatusBar style="dark" />

      <NavigationContainer>

        <Stack.Navigator

          screenOptions={{

            contentStyle: { backgroundColor: '#3f2f'},    

            headerStyle: { backgroundColor: '#991410' },

            headerTintColor: "white",

          }}

        >

          <Stack.Screen name="MealsCategories"

                        component={CategoriesScreen}

                        options={{

                          title:'All Categories',

                           }

                          }

                        />

          <Stack.Screen name="MealsOverview"

                        component={MealsOverviewScreen}

                        />

        </Stack.Navigator>

      </NavigationContainer>

    </>

   );

}
```


## Setting Navigation Options Dynamically












