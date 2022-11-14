## Section 17 Metoda klasy dekorator @classmethod

[#python/classmethod](app://obsidian.md/index.html#classmethod)

```py
class Phone:
	
	def show():
		print('Running...')

Phone.show() -> 'Running...'
p =Phone()
p.show() -> Error

```

```py
class Phone:
	
	def show(cls):
		print(f'Running...{cls}')

	show = classmethod(show)

Phone.show() -> 'Running...<class '__main__.Phone'>

p =Phone()
p.show() -> 'Running...<class '__main__.Phone'>

```

```py
class Phone:

	@classmethod
	def show(cls):
		print(f'Running...{cls}')

	
Phone.show() -> 'Running...<class '__main__.Phone'>

p =Phone()
p.show() -> 'Running...<class '__main__.Phone'>

```

```py
class Worker:
    instances = []
    
    def __init__(self):
        Worker.instances.append(self)
        
    @classmethod
    def count_instances(cls):
        return len(cls.instances)
        
Worker()
Worker()
Worker()
print(Worker.count_instances())
```