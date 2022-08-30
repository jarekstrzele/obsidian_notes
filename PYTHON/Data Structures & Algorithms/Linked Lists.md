
[[_Data Structures & Algorithms]]


---
# Linked Lists
- does not have indexes
- in the memory all of the nodes are going to be spread all over the place
- `head` points to the first element in the linked list
- `tail` points to the last item in the linked list
- each nodes point to the next one
- the last one pointe to the `None`

---
## Big O

### the end
- append to the end `O(1)`
- remove from the end `O(n)`, because `tail` has to point to the last list item, so you have to iterate by all list item
- 

### the beginning
- append to the begining `O(1)`
- remove from the begining `O(1)`

### the middle
- add to the middle of the list `O(n)`
- remove from the middle `O(n)`
- to find an item `O(n)`

---
## Under the hood
==NODE== =  value + pointer
is a dictionary `{"value": 4, "next": None}`


----
## Constructor

```python

class Node:
	def __init__(self, value):
		self.value = value
		self.next = None
	

class LinkedList:
	def __init__(self, value):
		"""create new Node"""
		new_node = Node(value)
		self.head = new_node
		self.tail = new_node
		self.length = 1

	def append(self, value):
		""" create new Node
			add Node to end
		"""

	def prepend(self, value):
		""" create new Node
			add node to beginning
		"""

	def insert(self, index, value):
		""" create new Node
			insert Node
		"""



		
```































