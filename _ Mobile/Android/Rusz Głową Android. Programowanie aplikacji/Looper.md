#kotlin/looper

>[!info] Looper
> `Looper` w Androidzie jest często używany do obsługi pętli komunikatów w wątku.
> Jest to mechanizm umożliwiający przetwarzanie wiadomości (komunikatów) w pętli wątku, umożliwiając tym samym przekazywanie zadań do wykonania w danym wątku. 
> Głównym zastosowaniem `Looper` jest ==obsługa zdarzeń w tle==, takich jak obsługa interakcji z użytkownikiem, obsługa sieci, czy inne operacje, które nie powinny blokować głównego wątku interfejsu użytkownika.

`Looper.getMainLooper()` to metoda dostępna w Androidzie, która zwraca instancję `Looper` dla głównego wątku (*main thread*) aplikacji.

W Androidzie, każde okno (*activity*) jest domyślnie powiązane z jednym wątkiem, który jest nazywany głównym wątkiem lub wątkiem interfejsu użytkownika (*UI thread*). Główny wątek obsługuje interakcje z interfejsem użytkownika, takie jak:
- dotyk, 
- rysowanie na ekranie, oraz 
- obsługę zdarzeń.

`Looper` jest mechanizmem, który umożliwia wątkowi przetwarzanie wiadomości w pętli. Główny wątek ma swój własny `Looper`, który pozwala na obsługę operacji w tle i planowanie zadań do wykonania na głównym wątku.











