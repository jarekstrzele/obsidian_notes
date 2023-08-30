[[_ C Sharp od Podstaw do WPF i XAML]]
#oop 

----
[[#Wstęp]]
[[#Konstruktory]]
[[#Metody]]



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














