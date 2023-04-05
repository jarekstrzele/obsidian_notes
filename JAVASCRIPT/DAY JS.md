#javascript  #dayjs 


------
# Using Daj.js in React
https://www.youtube.com/watch?v=vxBwVEhIzdA

https://day.js.org/
docs > plugins > relative time


`import dayjs from "dayjs"`

```jsx
import relativeTime from "dayjs/plugin/relativeTime" ;


dayjs.extend(relativeTime) ;
const commentTIme = dayjs(createdDate).fromNow() ; //createdDate comes from props

```

------------
# ogólnie
Biblioteka Day.js to biblioteka JavaScript do manipulacji datami i czasem. Oto kilka jej podstawowych funkcjonalności:

1.  Parsowanie daty i czasu: Biblioteka Day.js pozwala na łatwe parsowanie daty i czasu z różnych formatów. Można to zrobić za pomocą metody `dayjs()`, która przyjmuje ciąg znaków reprezentujący datę i czas oraz opcjonalnie format daty.
    
2.  Tworzenie nowych dat: Biblioteka Day.js umożliwia tworzenie nowych dat za pomocą konstruktora `dayjs()`. Można to zrobić, podając rok, miesiąc, dzień, godzinę, minutę i sekundę.
    
3.  Formatowanie daty i czasu: Day.js pozwala na łatwe formatowanie daty i czasu zgodnie z różnymi formatami. Można to zrobić za pomocą metody `format()`, która przyjmuje ciąg znaków reprezentujący format daty i czasu.
    
4.  Manipulowanie datą i czasem: Biblioteka Day.js umożliwia łatwe manipulowanie datami i czasem. Można to zrobić za pomocą różnych metod, takich jak `add()`, `subtract()`, `startOf()` i `endOf()`. Te metody pozwalają na dodawanie lub odejmowanie czasu do lub od daty, ustawianie daty i czasu na początek lub koniec określonego przedziału czasowego itp.
    
5.  Różnice między datami: Day.js umożliwia łatwe obliczanie różnic między datami. Można to zrobić za pomocą metody `diff()`, która przyjmuje drugą datę oraz jednostkę czasu (np. dni, godziny, minuty itp.) i zwraca różnicę między tymi dwoma datami.
    
6.  Lokalizacja daty i czasu: Day.js umożliwia łatwe lokalizowanie daty i czasu dla różnych stref czasowych i języków. Można to zrobić za pomocą metody `locale()`, która przyjmuje kod kraju i zwraca obiekt zawierający informacje o lokalizacji.
    
7.  Pluginy: Biblioteka Day.js umożliwia łatwe dodawanie dodatkowych funkcjonalności za pomocą pluginów. Istnieją pluginy do obsługi czasu względnego, formatowania daty i czasu zgodnie z zasadami języka naturalnego itp.


W bibliotece Day.js można zmieniać strefy czasowe w następujący sposób:

1.  Ustawienie domyślnej strefy czasowej: Można ustawić domyślną strefę czasową dla biblioteki Day.js za pomocą metody `dayjs.tz.setDefault()`. Metoda ta przyjmuje nazwę strefy czasowej (np. "Europe/Warsaw") i ustawia ją jako domyślną dla wszystkich operacji czasowych.



## strafy czasowe
`dayjs.tz.setDefault('Europe/Warsaw');`

2.  Tworzenie daty z określoną strefą czasową: Można tworzyć daty z określoną strefą czasową za pomocą metody `dayjs.tz()`. Metoda ta przyjmuje datę i nazwę strefy czasowej (np. "America/New_York") i zwraca datę w tej strefie czasowej.

javascriptCopy code

`const date = dayjs.tz('2023-04-05 12:00:00', 'America/New_York');`

3.  Konwersja daty między strefami czasowymi: Można konwertować daty między różnymi strefami czasowymi za pomocą metody `date.tz()`. Metoda ta przyjmuje nazwę docelowej strefy czasowej i zwraca datę w tej strefie czasowej.

javascriptCopy code

`const date = dayjs('2023-04-05 12:00:00'); const convertedDate = date.tz('Europe/London');`

4.  Formatowanie daty w określonej strefie czasowej: Można formatować daty w określonej strefie czasowej za pomocą metody `date.tz()`, a następnie metody `date.format()`. Metoda `date.tz()` przyjmuje nazwę strefy czasowej, a metoda `date.format()` przyjmuje format daty i zwraca sformatowaną datę w tej strefie czasowej.

javascriptCopy code

`const date = dayjs('2023-04-05 12:00:00'); const formattedDate = date.tz('Europe/Paris').format('DD/MM/YYYY HH:mm:ss');`


Oto kilka przykładów nazw stref czasowych, które mogą być używane jako argumenty w metodzie `dayjs.tz()`:

-   'Europe/London'
-   'America/New_York'
-   'Australia/Sydney'
-   'Asia/Tokyo'
-   'Africa/Johannesburg'
-   'Pacific/Honolulu'
-   'Antarctica/McMurdo'
-   'Etc/UTC'

Oprócz tych przykładów, biblioteka Day.js obsługuje również wiele innych nazw stref czasowych, które są zgodne z normą IANA Time Zone Database.






