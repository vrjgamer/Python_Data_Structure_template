# Linked List
There isn't a built-in data structure in Python that looks like a linked list.
Thankfully, it's easy to make classes that represent data structures in Python!

### Initializing a linked list
```python
#This is just one element of a linked list
class Element(object):
  def __init__(self, value):
    self.value = value
    self.next = None
#Now the main LinkedList Class
class LinkedList(object):
  def __init__(self, head=None):
    self.head = head
  # printing all values
  def print_all(self):
    printStr = ""
    current = self.head
    while current:
      printStr += (str(current.value) + ",")
      current = current.next
    print printStr
    return
  # get element at a position
  def get_at(self, position):
    current = self.head
    if self.head:
      while True:
      position -= 1
      if position == 0:
        return current
      else:
        if current.next:
          current = current.next
        else:
          break
    return None
```
### Appending elements to the end of a linked list
```python
#inside the linked list class
  def append(self, newElement):
    current = self.head
    if self.head: #checking if head exists or not 
      while current.next:
        current = current.next
      current.next = newElement
    else:
      self.head = newElement
```
### Inserting at a particular position in linked list
```python
#Insert an element at a position
  def insert(self, new_element, positon):
    previous = None
    current = self.head
    if current:
      while current.next:
        if position == 1:
          #you have reached the point
          break
        previous = current
        current = current.next 
        position -= 1
      if not(current == self.head) and position == 1:
        new_element.next = current
        previous.next = new_element
        return
    self.append(new_element)
    return  
```
### Deleting an element with a particular value
```python 
# delete an element with value
  def delete(self, value):
    """Delete the first node with a given value."""
    current = self.head
    previous = None
    if current:
      while current.next:
        if current.value == value:
          if current == self.head:
            self.head = current.next
          else:
            previous.next = current.next
            current.next = None
          break
        previous = current
        current = current.next
    return
```


## Entire Template
```python
#This is just one element of a linked list
class Element(object):
  def __init__(self, value):
    self.value = value
    self.next = None
#Now the main LinkedList Class
class LinkedList(object):
  def __init__(self, head=None):
    self.head = head
  # printing all values
  def print_all(self):
    printStr = ""
    current = self.head
    while current:
      printStr += (str(current.value) + ",")
      current = current.next
    print printStr
    return
  # get element at a position
  def get_at(self, position):
    current = self.head
    if self.head:
      while True:
      position -= 1
      if position == 0:
        return current
      else:
        if current.next:
          current = current.next
        else:
          break
    return None
#inside the linked list class
  def append(self, newElement):
    current = self.head
    if self.head: #checking if head exists or not 
      while current.next:
        current = current.next
      current.next = newElement
    else:
      self.head = newElement
#Insert an element at a position
  def insert(self, new_element, positon):
    previous = None
    current = self.head
    if current:
      while current.next:
        if position == 1:
          #you have reached the point
          break
        previous = current
        current = current.next 
        position -= 1
      if not(current == self.head) and position == 1:
        new_element.next = current
        previous.next = new_element
        return
    self.append(new_element)
    return  
# delete an element with value
  def delete(self, value):
    """Delete the first node with a given value."""
    current = self.head
    previous = None
    if current:
      while current.next:
        if current.value == value:
          if current == self.head:
            self.head = current.next
          else:
            previous.next = current.next
            current.next = None
          break
        previous = current
        current = current.next
    return

def main():
  
  return

if __name__ == "__main__":
  main()

```

