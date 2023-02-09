[[_ 0 Grafy w Pythonie]]

----
# Podgraf
podgraf:
- jego zbiór wierzchołków jest podzbiorem wierzchołków grafu
- jego zbiór krawędzi jest podzbiorem krawędzi grafu

**Przemyt słodkich bułek**
V = { Kacper, Dawid, Daniel, Michał, Wiktoria, ZdzisioPiekarz, JanuszKierowca}

E= {
( ZdzisioPiekarz, JanuszKierowca ) ,
( JanuszKierowca, Daniel ),
(JanuszKierowca, Wiktoria),
(Daniel, Dawid),
(Wikotria, Dawid),
(Daniel, Michał),
(Daniel, Kacper)
(WIkotria, Kacper),
(Kacper, Dawid),
(Dawid, Wikotria)
( Michał, Kacper )
}

Możemy wysłać zapytania:
- czy bułka jest przekazywana od Daniela do Michała, a potem od Michała do Kacpra?
- czy istnieje przemyt bułki od JanuszaKierowcy do Daniela, a potem do Michała lub Kacpra?
- czy istnieje przemyt od Wiktorii do Dawida, a potem od Dawida do Michała? (brak)
- czy istnieje przemyt od ZdzisiaPiekarza do Daniela, od Daniela do Jacka? (Jacka brak w grafie)






# Graf kompletny
> Graf, w którym każdy wierzchołek jest połączony z każdym innym

[Graf kompletny]

```python
V1 = {
    'A': ['B','C','D'],
    'B': ['A','C','D'],
    'C': ['A','B','D'],
    'D': ['A','B','C'],
}

  
V2 = {
    'A': ['B','C','D'],
    'B': ['A','C','D'],
    'C': ['A','D'],
    'D': ['A','B','C'],
}


def is_complete(V):
    for n in V.keys():
        if len(V[n]) != len(V)-1:
            return False
    return True

print(is_complete(V2))
```



# Myśliwy






# Najkrótsza droga





# graf cykliczny










# graf acykliczny











# drzewa 




# wyszukiwanie Depth First Search





























