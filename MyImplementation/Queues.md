# Queue (F.I.F.O.)
## In-built implementation 
Implementation of queue is already there in Python. To use the implementation just import "deque" from 'collections' package; 'collections.deque' is designed to have fast appends and pops from both ends.
```python
from collections import deque
queue = deque(["Eric", "John", "Michael"])
queue.append("Terry")           # Terry arrives
queue.append("Graham")          # Graham arrives
queue.popleft()                 # The first to arrive now leaves
# output is 'Eric'
queue.popleft()                 # The second to arrive now leaves
# output is 'John'
queue                           # Remaining queue in order of arrival
# output is deque(['Michael', 'Terry', 'Graham'])
```
for further documentation refer : https://docs.python.org/2/tutorial/datastructures.html#using-lists-as-queues, 

## Implementation using python list
```python
class Queue:
    def __init__(self, head=None):
        self.storage = [head]

    def enqueue(self, new_element):
        self.storage.append(new_element)
        return

    def peek(self):
        if len(self.storage) == 0:
            return None
        return self.storage[0]

    def dequeue(self):
        if len(self.storage) == 0:
            return None
        retElement = self.storage[0]
        del self.storage[0]
        return retElement
```
