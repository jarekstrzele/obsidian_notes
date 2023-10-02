[[_ C Sharp od Podstaw do WPF i XAML]]
#oop 

-----
[[1.1 Konstruktory]]







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


---

--------



# Klasy i metody abstrakcyjne










