#uselayouteffect
#react 
#react_native 

[[useEffect]]

`useLayoutEffect` to hook dostępny w React, który działa podobnie jak `useEffect`. Różnica między nimi polega na tym, kiedy dokładnie są wywoływane.

Hook `useLayoutEffect` pozwala na wykonywanie efektów ubocznych w momencie, gdy drzewo DOM jest już zaktualizowane, ale przed tym, jak przeglądarka przerysowuje widok. Innymi słowy, `useLayoutEffect` gwarantuje, że efekty uboczne będą wykonane przed renderowaniem w przeglądarce.

Dla porównania, `useEffect` działa w fazie wykonywania efektów, która ma miejsce po renderowaniu widoku i zaktualizowaniu drzewa DOM.

Podczas korzystania z `useLayoutEffect` należy zachować ostrożność, ponieważ zbyt wiele złożonych lub czasochłonnych operacji może spowodować opóźnienie w wyświetlaniu widoku. W większości przypadków lepiej jest korzystać z `useEffect`, chyba że specyfika projektu wymaga bezpośredniego dostępu do drzewa DOM przed jego przerysowaniem.


