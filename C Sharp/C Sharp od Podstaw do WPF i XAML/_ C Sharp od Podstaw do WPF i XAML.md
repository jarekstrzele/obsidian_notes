#udemy 

#clr
>[!info] CLR
> - Common Language Runtime (`.NET`) wspólna maszyna wirtualna język `.NET`
> - środowisko uruchomieniowe (część platformy *.NET Framework*)
> 	- zarządzanie pamięcią
> 	- obsługa wyjątków
> 	- ...
> - tłumaczy kod pośredni *IL* na kod maszynowy 
 > - dzięki niemu kod napisanych w różnych językach *.NET* może być uruchamiany na różnych systemach i sprzętach

#.net
> [!info] *.NET*
> -  to platforma programistyczna umożliwia
> 	- tworzenie i uruchamianie aplikacji na różnych platformach sprzętowych i systemach operacyjnych. 
> - .NET składa się z kilku komponentów, m.in.:
> 	- wspólnego języka pośredniego ([Common Intermediate Language](https://www.google.com/search?q=Common%20Intermediate%20Language) - CIL), który umożliwia tworzenie aplikacji w różnych językach programowania, które są przetwarzane na ten sam kod pośredni.
> 	- Kompilatorów języków programowania, takich jak [C#](https://www.google.com/search?q=C%23), [VB.NET](https://www.google.com/search?q=VB.NET), [F#](https://www.google.com/search?q=F%23), [C++/CLI](https://www.google.com/search?q=C%2B%2B%2FCLI), które umożliwiają tworzenie aplikacji w tych językach.
> 	- Środowiska uruchomieniowego, takiego jak [CLR](https://www.google.com/search?q=CLR) ([Common Language Runtime](https://www.google.com/search?q=Common%20Language%20Runtime)), które zapewniają wiele usług, takich jak zarządzanie pamięcią, obsługę wyjątków, wątków oraz automatyczne zarządzanie pamięcią.
> 	- Bibliotek klas, takich jak [.NET Framework Class Library](https://www.google.com/search?q=.NET%20Framework%20Class%20Library) (FCL), które zawierają gotowe komponenty, takie jak klasy do obsługi interfejsu użytkownika, sieci, wejścia/wyjścia, XML, bazy danych itp., co ułatwia i przyspiesza proces tworzenia aplikacji.


```c#
class Program
{
     static void Main(string[] args)
    {
        int a = 5;
        int b = 39;
        b = 111;
        Console.WriteLine("Hello, World!");

        Console.WriteLine("a = " + a);
        Console.WriteLine("b = " + b);

        /* 
        CAŁKOWITE
        ze znakiem: sbyte, short, int, long
        bez znaku: byte, ushort, uint, ulong

        ZMIENNOPRZECINKOWE
        float(32) double(64) decimal (128)

        BOOLEAN
        true false

        char x = 'a' ;

        string name = "Imię" ;
        
         */
        float xf = 1234.234234234234F;
        Console.WriteLine("float " + xf);

        double xdouble = 1234.234234234234F;
        Console.WriteLine("double " + xdouble);

        decimal xdecimal = 2131231.234234234231231234M;
        Console.WriteLine("decimal " + xdecimal);


        const double PI = 3.14;
    }

}
```


---
# Działanie
`+ -  / * %`

`a / (double)b ;`

`++x`  `--x`
`x++` `x--`

`a += 2 ;`
`a -= 10 ;`

---
# if


```c#
if () {}
```








