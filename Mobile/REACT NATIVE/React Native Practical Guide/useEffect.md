#useEffect
#react 
#react_native  

[[useLayoutEffect]]


`useEffect` jest jednym z hooków dostępnych w React, który umożliwia wykonywanie efektów ubocznych (ang. side effects) w komponentach funkcyjnych.

Efekty uboczne to operacje, które wychodzą poza renderowanie widoku i mogą obejmować takie rzeczy jak:

-   Pobieranie danych z zewnętrznego źródła (np. API)
-   Manipulacja DOM
-   Subskrybowanie i odsubskrybowanie zdarzeń (np. zdarzenia przeglądarki)
-   Zmiana stanu za pomocą funkcji `setState`

Hook `useEffect` przyjmuje dwa argumenty:

1.  Funkcję zwrotną (callback), która definiuje efekt uboczny. Ta funkcja będzie wywoływana za każdym razem, gdy komponent zostanie wyrenderowany. Funkcja ta może zwracać inną funkcję, która będzie wykonana przy odmontowywaniu komponentu.
    
2.  Tablicę zależności, która określa, kiedy funkcja zwrotna powinna zostać wywołana. Jeśli tablica jest pusta, efekt zostanie wykonany tylko raz, podczas pierwszego renderowania komponentu. Jeśli tablica zawiera wartości, które są zależne od stanu komponentu, efekt zostanie wykonany ponownie, gdy któreś z tych zależności ulegnie zmianie.
    

Dzięki hookowi `useEffect` możesz wykonywać operacje, które wychodzą poza renderowanie widoku, a jednocześnie zapewniają, że stan komponentu jest zawsze zsynchronizowany z wykonywanymi operacjami.

