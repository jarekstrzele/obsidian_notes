#react_native  #hook #useNavigation

`useNavigation` jest hookiem dostarczonym przez bibliotekę `react-navigation` w React Native, który pozwala na dostęp do funkcjonalności nawigacji w aplikacji bez konieczności przekazywania ich przez `props`.

Hook ten jest przydatny, gdy potrzebujesz programistycznie nawigować pomiędzy różnymi ekranami w aplikacji, np. przejść do innego ekranu po kliknięciu przycisku. Aby go użyć, wystarczy zaimportować go z biblioteki `react-navigation` i wywołać go w komponencie:
```javascript
import { useNavigation } from '@react-navigation/native';

function SomeComponent() {
  const navigation = useNavigation();

  return (
    <View>
      <Button
        title="Go to another screen"
        onPress={() => navigation.navigate('AnotherScreen')}
      />
    </View>
  );
}

```
W powyższym przykładzie, `useNavigation` jest wywoływany w komponencie `SomeComponent` i udostępnia funkcję `navigate`, którą można wywołać, aby przejść do innego ekranu o nazwie `AnotherScreen`.
