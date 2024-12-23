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



# Myśliwy -ścieżka w grafie

## Breadth First Check - przeszukiwanie wszerz
Node1- Czy znasz Myśliwego? nie. A Kogoś znasz? Tak->Node2 -Czy ... 


np. 
	E--D1
		D1--D2
		D1--P
		D1--D2
		D2--P
					P-K
					P-Q
					P-H
						H-K
						
Czy istnieje droga z E do H?
- Hej D1 czy jesteś myśliwym (H)?
- Nie
- A znasz kogoś?
- tak, znam P i D2
- Hej D2 czy jesteś myśliwym?
- nie, 
- 
dwie listy
*to check*                        *visited*
D1                                      --
D2, P                                 D1
P                                        D1  D2
P D1 P                              
....

Przechodzimy przez wierchołki pytając o sąsiadów danego wierzchołka, aż znadziemy cel

```python
V = {
    'P': ['K', 'Q', 'H'],
    'D1': ['D2', 'E', 'P'],
    'D2': ['D1', 'P'],
    'K': ['P', 'Q'],
    'Q': ['P', 'K', 'H'],
    'H': ['P', 'Q'],
    'E': ['D1'],
}

V2 = {
    'A' : ['B', 'C'],
    'B' : ['D'],
    'C' : ['D'],
    'D' :['A']
}


def is_path_between(V, source, dest):
    list_to_check = [source]
    list_visited = []

    while list_to_check:
        curr_node = list_to_check.pop(0)
        if curr_node == dest:
            return True
        else:
             if curr_node not in list_visited:
                 list_visited.append(curr_node)
                 list_to_check.extend(V[curr_node])

    return False
  

print(is_path_between(V, 'E', 'H'))

for s in V.keys():
    for d in V.keys():
        if s != d:
            print(f' Path {s} - {d} - {is_path_between(V,s,d)}')
```

----------
# Najkrótsza droga
```python
V = {
    'P': [ 'D1', 'D2', 'K', 'Q', 'H'],
    'D1': ['D2', 'E', 'P'],
    'D2': ['D1', 'P'],
    'K': ['P', 'Q'],
    'Q': ['P', 'K', 'H'],
    'H': ['P', 'Q'],
    'E': ['D1'],
}
 

V2 = {
    'A' : ['B', 'C'],
    'B' : ['D'],
    'C' : ['D'],
    'D' :['A']
}

  

def is_path_between(V, source, dest):
    list_to_check = [source]
    list_visited = []
  
    while list_to_check:
        curr_path = list_to_check.pop(0)
        curr_node = curr_path[-1]
        if curr_node == dest:
            return curr_path
        else:
             if curr_node not in list_visited:
                 list_visited.append(curr_node)
                 for n in V[curr_node]:
                     new_path = curr_path.copy()
                     new_path.append(n)
                     list_to_check.append(new_path)

    return []

print(is_path_between(V, 'E', 'H'))

for s in V.keys():
    for d in V.keys():
        if s != d:
            print(f' Path {s} - {d} - {is_path_between(V,s,d)}')
```

--------
# graf cykliczny









---------------
# graf acykliczny










-----------------
# drzewa 
>[!info] drzewo
>To graf acykliczny (brak 'pętelek') połączony (od każdego węzła grafu przejdziesz do każdego innego węzła)


![[graf-drzewo-wyjazd.excalidraw | 600]]


```python
wyjazd = { 
    'ojciec' : [ 'samochód', 'matka', 'dzieci'],
    'samochód': [ 'paliwo', 'hamulce'],
    'paliwo': [],
    'hamulce' :[],
    'matka':['jedzenie', 'ubrania', 'zdrowie'],
    'jedzenie':[],
    'ubrania':[],
    'zdrowie':[],
    'dzieci':['smartphone', 'power bank'],
    'smartphone': [],
    'power bank':[]
    
}

status = {
    'paliwo': True,
    'hamulce': True,
    'jedzenie': True,
    'ubrania': True,
    'zdrowie': True,
    'smartphone': False,
    'power bank': True
}

def czy_wyjezdzamy(graf, status, start):
    
    if graf[start]:
        for wiezcholek in graf[start]:
            if not czy_wyjezdzamy(graf, status, wiezcholek):
                print(f'{start} - False')
                return False
        print(f'{start} - True')
        return True
    else:
        print(f'{start} {status[start]}')
        return status[start]
    

czy_wyjezdzamy(wyjazd, status, 'ojciec')
```

--------------------------------
# wyszukiwanie Depth First Search

Ten algorytm nie ogranicza się tylko do drzew, jak poprzedni.

![[graf_DFS.excalidraw | 600]]


```python
V = {
'tygrysek': ['prosiaczek', 'puchatek'],
'prosiaczek': ['tygrysek', 'puchatek', 'sowa', 'maleństwo'],
'puchatek' :['tygrysek', 'prosiaczek', 'krzyś'],
'maleństwo' :['prosiaczek', 'mama', 'hefalump'],
'sowa' :['prosiaczek', 'hefalump', 'krzyś'],
'krzyś': ['puchatek', 'sowa'],
'mama': ['maleństwo', 'hefalump'],
'hefalump': ['maleństwo', 'mama', 'sowa']
	 
}
```









