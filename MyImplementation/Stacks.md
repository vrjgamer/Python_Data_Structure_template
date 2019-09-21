# Stacks
The built-in funtions in Python list turn it into a stack. pop() is a given function, and append() is equivalent to a push function.

## Implementation using Linked List
```python
class Element(object):
    def __init__(self, value):
        self.value = value
        self.next = None
# linked list internally
class Stacks(object):
    def __init__(self, head=None):
        self.head = head
        
    def append(self, new_element):
        current = self.head
        if self.head:
            while current.next:
                current = current.next
            current.next = new_element
        else:
            self.head = new_element

    def push(self, new_element):
        # push element to the top-of-stack
        new_element.next = self.head
        self.head = new_element
        return

    def pop(self):
        # pop the top-most-element
        current = self.head
        if current:
            self.head = current.next
            current.next = None
        else:
            self.head = None
        return current
```

