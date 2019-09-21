# Merge Sort
### Space complexity
not inplace, O(n) auxilary space required
### Time complexity
worst case -> O(nlog(n)) <br/>
avg. case -> O(nlog(n)) <br/>
best case -> O(nlog(n)) <br/>

```python

def merge_sort(array):
    #base case a list of 0 or 1 element is already sorted
    if len(array) <= 1:
        return array
    
    # First, divide the list into equal-sized sublists
    # consisting of the first half and second half of the list.
    left = []
    right = []
    for index, value in enumerate(array):
        if index < (len(array)/2):
            left.append(value)
        else:
            right.append(value)
    
    left = merge_sort(left)
    right = merge_sort(right)
    
    return merge(left, right)

def merge(left, right):
    result = []
    while len(left) != 0 and len(right) != 0:
        if left[0] <= right[0]:
            result.append(left[0])
            left = left[1:]
        else:
            result.append(right[0])
            right = right[1:]
    
    # Either left or right may have elements left; consume them.
    # (Only one of the following loops will actually be entered.)
    while len(left) != 0:
        result.append(left[0])
        left = left[1:]
        
    while len(right) != 0:
        result.append(right[0])
        right = right[1:]

    return result
# source pseudocode : https://en.wikipedia.org/wiki/Merge_sort
```
