#android/context

W Androidzie, klasa `Context` jest fundamentalnym elementem, reprezentującym środowisko aplikacji. Oto kilka kluczowych aspektów związanych z klasą `Context`:

1. **Środowisko Aplikacji:**
       - `Context` dostarcza dostępu do zasobów i funkcji związanego z daną aplikacją Androida. To obejmuje dostęp do plików, dostęp do *SharedPreferences*, dostęp do usług systemowych i wiele innych.
2. **Rodzaje Contextu:**
       - Istnieje kilka różnych implementacji `Context` w Androidzie, takich jak `Activity`, `Service`, `Application`, `ApplicationContext` itp. Każda z tych klas dziedziczy po klasie `Context` i dostarcza specyficzne dla swojego kontekstu funkcje.
3. **Dostęp do Zasobów:**
       - Poprzez `Context`, aplikacja ma dostęp do różnych zasobów, takich jak pliki, ciągi znaków, kolory, style itp. Metody takie jak `getResources()`, `getString()`, `getAssets()` pozwalają na dostęp do tych zasobów.
4. **Uruchamianie Komponentów:**
       - `Context` umożliwia uruchamianie różnych komponentów systemu Android, takich jak aktywności (`startActivity()`), usługi (`startService()`), itp.
5. **Broadcasts:**
       - `Context` pozwala na nadawanie i odbieranie komunikatów radiowych (broadcasts), co umożliwia komunikację między różnymi komponentami aplikacji.
6. **Zarządzanie Życiem Aplikacji:**
       - `Context` umożliwia zarządzanie cyklem życia aplikacji, dzięki czemu można uzyskać dostęp do informacji o stanie aplikacji i reagować na zdarzenia związane z jej cyklem życia.
7. **Dostęp do SharedPreferences:**
       - `Context` pozwala na korzystanie z `SharedPreferences`, co umożliwia przechowywanie danych w trybie klucz-wartość.
8. **Dostęp do Systemowego Service Managera:**
       - `Context` umożliwia dostęp do różnych usług systemowych, takich jak zarządzanie urządzeniem, dostęp do systemowego Service Managera itp.

Przez to wszechstronne API, klasa `Context` stanowi kluczowy punkt dostępu do wielu funkcji i zasobów w aplikacjach Androida. W praktyce, różne klasy komponentów Androida, takie jak `Activity` czy `Service`, dziedziczą z klasy `Context`, co umożliwia im korzystanie z tych funkcji.














