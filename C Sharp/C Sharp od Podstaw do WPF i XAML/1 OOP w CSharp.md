[[_ C Sharp od Podstaw do WPF i XAML]]
#oop 

-----
[[1.1 Konstruktory]]
[[1.2 Metody i Właściwości]]
[[1.3 Klasy zagnieżdżone]]
[[1.4 Dziedziczenie]]
[[1.5 Polimorfizm i rzutowanie]]
[[1.6 Klasy abstrakcyjne]]
[[1.7 Interfejsy]]
[[1.8. Klasy i metody zapieczętowane (sealed)]]


---------------


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

