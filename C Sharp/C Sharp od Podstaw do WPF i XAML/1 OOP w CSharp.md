[[_ C Sharp od Podstaw do WPF i XAML]]
#oop 

----
[[#Wstęp]]
[[#Konstruktory]]
[[#Metody]] 
[[#Konstruktor statyczny]]
[[#Konstruktory kopiujące]]
[[#klasy zagnieżdżone]]


-----

# Wstęp

==atrybuty obiektów powinny zostać prywatne (domyślnie)==

```c#
class Program
{
     static void Main(string[] args)
    {
        Czlowiek a = new Czlowiek();
        Console.WriteLine(a.getName());
        a.setName("Wiola");
        Console.WriteLine(a.getName());
    }
}

class Czlowiek
{
    string name = "Arek";

    public string getName() 
    { 
        return this.name; 
    }

    public void setName(string name)
    {
        this.name = name;
    }

}
```


---
# Konstruktory

```c#
class Program
{
     static void Main(string[] args)
    {
        Console.WriteLine(Gracz.NastepnyId);

        Gracz g = new Gracz("Śmierdzioch");
        //Console.WriteLine(g.nick);
        Console.WriteLine(g.Nick);
        g.Nick = "Nowy nick";
        Console.WriteLine(g.Nick);

        Gracz[] gracz = new Gracz[3];
        gracz[0] = new Gracz("Morf");
        gracz[1] = new Gracz("Tobi");
        Console.WriteLine(gracz[1].Id);


    }
}

class Gracz
{
    //public string nick;
    int id;
    static int nastepnyId = 0;
    string nick;

    public Gracz()
    {
        nick = "";
        id = 0;
    }
    public Gracz(string nick)
    {
        this.nick = nick;
        nastepnyId++;
        this.id = nastepnyId;
    }

    public string Nick
    { 
        get 
        { 
            return nick; 
        }
        
        set
        {
            this.nick = value;
        }
    }

    public int Id
    {

        get
        {
            return this.id;
        }
    }

    public static int NastepnyId
    {
        get
        {
            return nastepnyId;
        }
    }

}
```


```c#
class Program
{
     static void Main(string[] args)
    {
        Console.WriteLine(Matematyka.dodaj(10, 20));
        Console.WriteLine(Matematyka.PI);
    }
}


class Matematyka
{
    public static int dodaj(int a, int b)
    {
        return a + b;
    }

    public static readonly double PI = 3.14;
}
```


--------
# Metody

## Przekazywanie przez wartość lub przez referencję

```c#
class Program
{
    static void Main(string[] args)
    {
        int a = 10;

         Math.IncreaseBy5(a);
 Console.WriteLine("po wykonaniu IncreaseBy5 (kopia): = " + a); // --> 10, bo przekazujemy przez wartość (kopię)

 Math.IncreaseBy5ByReference( ref a); // przekazuję adres pamięci
 Console.WriteLine("po przekazaniu referencji a= " + a);
       
        Console.ReadLine();

    }
}

class Math
{
    public static int Abs(int x)
    {
        if (x < 0)
            return x * (-1);
        return x;
    }

    public static int IncreaseBy5(int nr)
    {
        nr += 5;
        return nr;
    }

    public static int IncreaseBy5ByReference(ref int nr)
    {
        nr += 5;
        return nr;
    }
}
```

### z `overloading`
funkcje mają taką samą nazwę, ale różnią się parametrami

cały kod jak powyżej, zmienia się końcówka
```c#
 public static int IncreaseBy5(int nr)
 {
     nr += 5;

     return nr;
 }

 static int IncreaseBy5(ref int nr)
 {
     nr += 5;

     return nr;
 }
```

### `out`
#csharp/out
> słowo kluczowe `out` używane jest w deklaracji parametrów metody i służy do przekazywania argumentów przez referencję z dodatkowym wymogiem, że metoda musi przypisać wartość do przekazanego parametru.

```c#
class Program
{
    static void Main(string[] args)
    {
        int aa;
        Math.zeruj(out aa);
        Console.WriteLine(aa);


    }
}

class Math
{

    public static void zeruj(out int x)
    {
        x = 0;
    }
```

### wiele argumentów `params`
```c#
class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine(Math.Dodaj(1, 1, 1));
        Console.WriteLine(Math.Dodaj(1, 1, 1, 1, 1, 1, 1));


    }
}

class Math
{
    public static int Dodaj(params int[] args)
    {
        int suma = 0;
        for (int i = 0; i < args.Length; i++)
        {
            suma = suma + args[i];
        }

		// foreach (int i in args)
		// {
		   // suma += i;
		//}

        return suma;
    }
}
```

### parametry domyślne

```c#
class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine(Math.Poteguj(2, 3));
        Console.WriteLine(Math.Poteguj(2));
    }
}

class Math
{
    public static int Poteguj(int podstawa, int wykladnik = 2)
    {
        int tmp = 1;

        for (int i = 0;i < wykladnik; i++)
        {
            tmp *= podstawa;
        }

        return tmp;
    }
```


### zaimplementowane Właściwości
ręczne pisanie Właściwości
```c#
class Obywatel 
{
	private string imie;
	public string Imie
	{
		get 
		{
			return imie;
		}
		set 
		{
			imie = value;
		}
	}
}
```


automatycznie
```c#
using System;
using System.Collections.Generic;

class Program {
  public static void Main (string[] args) {

    //przekazywanie argumentów nazwanych imie: 
    Obywatel ob1 = new Obywatel(nazwisko: "Nowak", imie: "Jan") ;
    // ob1.Imie = "Tomek" ; //error
    Console.WriteLine(ob1.Imie) ;
    
  }
}

  class Obywatel
  {
    public string Imie {get; private set;} // musi być get; set; z private imie jest niezmienialne
    public string Nazwisko {get; set;} 

    public Obywatel(string imie, string nazwisko){
      this.Imie = imie ;
      this.Nazwisko=nazwisko ;
      
    }
  }
```


---

# Konstruktor statyczny
- Wywoływany jest przed stworzeniem obiektu
- nie jest dziedziczony
- Konstruktor statyczny w C# jest wywoływany automatycznie przed użyciem klasy lub przed utworzeniem instancji klasy. Służy do inicjalizacji statycznych pól klasy lub do wykonania innych operacji, które mają być wykonane tylko raz.
- nie przyjmuje żadnych argumentów i nie zwraca żadnych wartości

```C#
using System;

class Program
{
    public static void Main()
    {
        Console.WriteLine(Welcomer.Msg);
        Console.WriteLine(Welcomer.Msg);
        Console.WriteLine(Welcomer.Msg);
        Console.WriteLine(Welcomer.Msg);

    }
}

class Welcomer
{
    public static string Msg
    {
        get;
        private set;
    }

    static Welcomer()
    {
        Console.WriteLine("Uruchomiłem Welcomera");
        DateTime now = DateTime.Now;

        if (now.Hour < 17)
        {
            Msg = "Dzień dobry";
        }
        else
        {
            Msg = "Dobry wieczór";
        }
    }
}
```

inny przykład
```c#
using System;

public class MojaKlasa
{
    // Statyczne pole
    public static int Licznik { get; set; }

    // Konstruktor statyczny
    static MojaKlasa()
    {
        Licznik = 0;
        Console.WriteLine("Konstruktor statyczny został wywołany.");
    }

    // Metoda statyczna, która zwiększa wartość Licznik
    public static void InkrementujLicznik()
    {
        Licznik++;
    }
}

class Program
{
    static void Main()
    {
        // Możemy używać klasy i jej składowych statycznych bez tworzenia instancji
        MojaKlasa.InkrementujLicznik();
        MojaKlasa.InkrementujLicznik();

        Console.WriteLine($"Wartość Licznik: {MojaKlasa.Licznik}");
    }
}

```

# Konstrutor wywołujący inne konstruktory

```c#
using System;
using System.ComponentModel;

class Program
{
    public static void Main()
    {

        Car maluch = new Car("super wóz");
        Console.WriteLine(maluch.numOfWheels);
    }
}

class Car
{
    public string description;
    public byte numOfWheels;

    public Car(string desc, byte numOfWheels) {
        this.description = desc;
        this.numOfWheels = numOfWheels;
    }

    // konstruktor wywołujący inny konstruktor
    public Car(string desc) : this(desc, 4)
    {
        Console.WriteLine("Make a car with 4 wheels");
    }

}

```

# Konstruktory kopiujące
klasa `Car` z poprzedniego kodu
```c#
class Program
{
    public static void Main()
    {

        // kopiowanie wartości
        int a = 10;
        int b = a;
        b = 999;
        Console.WriteLine("a = " + a);
        Console.WriteLine("b = " + b);
        Console.WriteLine("a = " + a);

        // przypisanie referencji
        Car maluch = new Car("super wóz");
        Car polonez = maluch;
        Console.WriteLine("maluch: " + maluch.description);
        polonez.description = "Samochów biodegradowalny";
        Console.WriteLine("polonez: " + polonez.description);
        Console.WriteLine("maluch (po zmianie poloneza): " + maluch.description);

    }
}
```
aby `Car polonez = maluch;` było kopiowanie obiektu, a nie przypisaniem referencji należy zdefiniować konstruktor kopiujący
czyli do klasy `Car` dopisujemy nowy konstrukotr
```c#
    public Car(Car samochod)
    {
        this.description = samochod.description;
        this.numOfWheels = samochod.numOfWheels;
    }
```

```c#
class Program
{
    public static void Main()
    {

        Car maluch = new Car("super wóz");

		//kopiujemy obiekt
        Car polonez = new Car(maluch);
        Console.WriteLine("maluch: " + maluch.description);
        polonez.description = "Samochów biodegradowalny";
        Console.WriteLine("polonez: " + polonez.description);
        Console.WriteLine("maluch (po zmianie poloneza): " + maluch.description);

    }
}

```

--------
# klasy zagnieżdżone
```c#
class Program
{
     static void Main(string[] args)
    {
        Car car = new Car();

    }
}


class Car
{
    private class Engine
    {
        public uint Power;
        public Engine(uint power = 500)
        { 
            this.Power = power;
            Console.WriteLine("I am from the engin constructor");
        }
    }

    public Car()
    {
        this.engine = new Engine();
        
        Console.WriteLine("I am from the car constructor");
    }

    public uint getPower()
    {
        return this.engine.Power;
    }

    private Engine engine; 
}
```




# Dziedziczenie
plik `Punk.cs`
```c#
 public class Punkt
 {
    public int X
    {
       /*get; private set;*/
       get; protected set; // te, które dziedziczą mogą ustawiać nową wartość
   }
    public int Y
    {
       /*get; private set;*/
       get; protected set; // te, które dziedziczą mogą ustawiać nową wartość

   }

   public Punkt()
   {
   Console.WriteLine("Jestem BEZargumentowym konstruktorem" + " klasy PUNKT");
           X = 0;
           Y = 0;  
    }
   public Punkt(int x, int y)
   {
      Console.WriteLine("Jestem DWUargumentowym konstruktorem " + " klasy PUNKT");
           X = x;
           Y = y;
    }
}
```

Plik `Puntt3d.cs`
```c#
public class Punkt3D : Punkt
{
	public int Z {
        /*get; private set;*/
        get; protected set; // te, które dziedziczą mogą ustawiać nową wartość

    }

    public Punkt3D()
	{
	}

	public Punkt3D(int x, int y, int z) : base(x, y)
	{
		this.Z = z;
	}

    public string wyswietlKoordynaty()
    {
        return $"{base.wyswietlKoordynaty()} Z={ this.Z}" ;
    }
}
```







