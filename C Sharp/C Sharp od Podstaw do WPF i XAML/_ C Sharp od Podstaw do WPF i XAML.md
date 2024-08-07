#udemy  #csharp 

----
[[1 OOP w CSharp]]
[[8 Aplikacje WPF]]
[[3 Układ komponentów]]
[[4 Tworzenie aplikacji WPF]]





------
[[#Działanie]]
[[#if]]
[[#Pętle]]
[[#Tablice]]
[[#tablice wielowymiarowe]]
[[#`foreach`]]






-------



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
if ( warunek ) {

} else {

}
```


```c#
string nazwaKraju = "PL" ;

switch (nazwaKraju)
{
	case "PL":
		Console.WriteLine("Jesteś  z Polski") ;
		break ;
	case "EN":
	case "UK":
		Console.WriteLine("Jesteś z  Angli") ;
		break ;
	default:
		// ....
		break ;
}
```


`zmienn = (warunek) ? wartość zmiennej gdy warunek true : wartość zmiennej, gdy warunek false`

# Pętle

```c#
for (int i= 0; i < 3; i++){
 // some code
}
```
`i` jest lokalne, istnieje tylko w pętli `for`

```c#
while (warunek) 
{

}

do
{

}while (warunek) ;
```

--------
# Tablice
#csharp/table

>Tablice w C# są kolekcjami o stałej długości. Po zadeklarowaniu tablicy, nie można zmienić jej rozmiaru. W przypadku `int[] lista = {1, 2, 3, 4};`, tablica ma długość 4.


```c#

class Program
{
     static void Main(string[] args)
    {
        //int[] tab;
        //tab = new int[10];
        int[] tab = new int[10];

        tab[0] = 3;
        tab[1] = 13;
        tab[2] = 113;
        tab[3] = 2223;
        
        for(int i = 0; i < tab.Length; i++)
        {
            Console.WriteLine(tab[i]);
        }

        Console.ReadLine(); //czeka na enter

        int[] ciag = new int[] { 99, 22, 10, 20 };
        for(int i = 0;i < ciag.Length;i++)
        {
            Console.WriteLine(ciag[i]);       
        }

        int[] ciag2 = { 12, 23, 456, 66 };

        
    }

}
```

------
# tablice wielowymiarowe
`int[,] nazwa = new int[4,3]`   tablica o 4 rzędach i trzech kolumnach

`string[,] tab2D = new string[4,3]` tablica dwuwymiarowa 4x3

```c#
class Program
{
     static void Main(string[] args)
    {
        string[,] tab2D = new string[4, 3];

        for(int i = 0; i < tab2D.GetLength(0); i++)
            for(int j = 0; j < tab2D.GetLength(1); j++)
            {
                tab2D[i, j] ="tab [" + i + "," + j + "]  ";
            }

        for (int i = 0; i < tab2D.GetLength(0); i++)
        {
            for (int j = 0; j < tab2D.GetLength(1); j++)
            {
                Console.Write(tab2D[i, j]);
            }
            Console.WriteLine();
        }
    }

}
```

==tablica wyszczerbiona==

```c#
class Program
{
     static void Main(string[] args)
    {
        int[][] jaggedArray = new int[3][];

        jaggedArray[0] = new int[] { 1, 2, 3, 4 };
        jaggedArray[1] = new int[] { 10, 1, 10, 2, 10, 3 };
        jaggedArray[2] = new int[] { 1, 2 };

        for(int i = 0; i < jaggedArray.GetLength(0); i++)
        {
            for (int j = 0; j < jaggedArray[i].Length; j++)
            {
                Console.Write(jaggedArray[i][j] + " ");
            }
            Console.WriteLine();
        }

    }

}
```


---
# `foreach`
#csharp/foreach

```c#
class Program
{
     static void Main(string[] args)
    {
        int[] tab = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, };

        foreach (int i in tab)
        {
            Console.WriteLine(i);
        }
        
    }

}
```

# Lista
#csharp/list
> Listy w C# są dynamicznymi kolekcjami, które mogą zmieniać swój rozmiar w trakcie działania programu. Możesz dodawać, usuwać i modyfikować elementy w liście w dowolnym momencie.


## modify
```c#
List<int> lista = new List<int> {1, 2, 3};
lista[1] = 4; // Zmienia wartość elementu na indeksie 1 na 4

List<int> lista = new List<int> {1, 2, 3};
lista.Insert(1, 4); // Wstawia liczbę 4 na indeksie 1, lista staje się {1, 4, 2, 3}


```

## remove
```c#
List<int> lista = new List<int> {1, 2, 3, 4, 5};
lista.Remove(3); // Usuwa pierwsze wystąpienie liczby 3 z listy

List<int> lista = new List<int> {1, 2, 3, 4, 5};
lista.RemoveAt(2); // Usuwa element na indeksie 2 (czyli liczbę 3)

List<int> lista = new List<int> {1, 2, 3, 4, 5};
lista.RemoveAll(x => x > 3); // Usuwa wszystkie elementy większe niż 3

List<int> lista = new List<int> {1, 2, 3, 4, 5};
lista.RemoveRange(1, 3); // Usuwa elementy od indeksu 1 do 3 (włącznie)

List<int> lista = new List<int> {1, 2, 3, 4, 5};
lista.Clear(); // Usuwa wszystkie elementy z listy, lista staje się pusta


```






