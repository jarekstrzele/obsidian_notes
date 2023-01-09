
## Section 18 Metoda statyczna - dekorator ==@staticmethod==

#staticmethod

- nie jest związana ani z klasą ani z obiektem
- to zwykła funkcja, ale występująca w przestrzeni nazw klasy
---

```py
import time

class Phone:

	@staticmethod
	def get_current_time():
		return time.strftime('%H:%M:%S', time.localtime())


	# get_current_time = staticmethod(get_current_time)

Phone.get_current_time() -> ok
p = Phone()
p.get_current_time()   -> ok
```

```py

import time

class Container:

	@staticmethod
	def get_current_time():
		return time.strftime('%H:%M:%S', time.localtime())
```

---
