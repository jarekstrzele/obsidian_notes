#csharp #linq  
# Przykłady użycia LINQ:

- **Filtrowanie kolekcji:**
    
    csharpCopy code
    
    `var filtered = people.Where(person => person.Age > 18);`
    
- **Sortowanie:**
    
    csharpCopy code
    
    `var sorted = people.OrderBy(person => person.LastName).ThenBy(person => person.FirstName);`
    
- **Agregacja:**
    
    csharpCopy code
    
    `var totalAge = people.Sum(person => person.Age);`
    
- **Pobieranie unikalnych wartości:**
    
    csharpCopy code
    
    `var uniqueAges = people.Select(person => person.Age).Distinct();`
    
- **Połączenia (join) i grupowanie:**
    
    csharpCopy code
    
    `var groupedByAge = people.GroupBy(person => person.Age);`