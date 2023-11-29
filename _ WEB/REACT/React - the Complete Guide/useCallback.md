#react #hook #usecallback  
`useCallback` to hook w React, który służy do optymalizacji wydajności komponentów funkcyjnych poprzez pamiętanie i ponowne wykorzystywanie referencji do funkcji.

Głównym zastosowaniem `useCallback` jest unikanie niepotrzebnego ponownego renderowania komponentów, które używają funkcji jako propsów. Bez użycia `useCallback`, każde wywołanie `setState` lub zmiana propsów zmuszałaby komponent do ponownego renderowania, co może prowadzić do spadku wydajności w aplikacjach złożonych.

Używając `useCallback`, możemy przekazać funkcję jako zależność, która jest zapamiętywana przez hook i zwrócona przez niego. Jeśli komponent zostanie ponownie wyrenderowany, hook zwróci tę samą referencję funkcji, co pozwala uniknąć niepotrzebnego ponownego renderowania potomków, którzy używają tej samej funkcji jako props.

Oto przykład użycia `useCallback`:

jsx

`import React, { useCallback } from 'react';  function MyComponent(props) {   const handleClick = useCallback(() => {     console.log('Button clicked!');   }, []);    return (     <button onClick={handleClick}>Click me</button>   ); }`

W tym przykładzie, `useCallback` jest używany do zapamiętania funkcji `handleClick`, co pozwala uniknąć niepotrzebnego ponownego renderowania komponentu, gdy propsy się zmieniają. `[]` to pusta tablica zależności, co oznacza, że hook będzie zwracał zawsze tę samą funkcję i nie będzie jej ponownie renderować.


