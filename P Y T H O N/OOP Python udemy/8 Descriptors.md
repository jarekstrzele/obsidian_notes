[[_ 0 Python OOP]]

> W Pythonie deskryptory to specjalne klasy, które umożliwiają kontrolę dostępu do atrybutów klasy poprzez przesłanianie standardowych metod takich jak `__get__`, `__set__` i `__delete__`. Deskryptory są często wykorzystywane w programowaniu obiektowym do tworzenia bardziej zaawansowanych mechanizmów dostępu do atrybutów klasy, takich jak walidacja wartości czy automatyczne przeliczanie wartości.

control the semantics of attribute access in Python - you can
- intercept  the basic attribute and operation  (get, set, delete)
- customize the basic attribute and operation (get, set,delete)

# Attribute LookupChain Review
1. look in the instance(i.e. object) `__dict__` for a key with the attribute's name
2. look in hte instance;s type (i.e. class) `__dict__` for a key with the attribute'sname
3. look in the instance;s parent type (i..e. parent class) `__dict__` for a key with the attribute's name
4. if not found, repeat for each parent type in mro order
5. if not found, raise AttributeError












