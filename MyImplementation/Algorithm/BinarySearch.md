# Binary Search Algorithm
time complexity : O(log(n))
assumption is that the input_array is in increasing order and '-1' return value denotes a miss in the array
```python
def binary_search(input_array, value):
    if len(input_array) == 0:
        return -1
    top = 0
    bottom = len(input_array) - 1
    mid = (top + bottom)/2
    while top < bottom:
        if input_array[mid] == value:
            return mid
        elif input_array[mid] < value:
            top = mid + 1
        else:
            bottom = mid
        mid = (top + bottom)/2
    return -1
```
