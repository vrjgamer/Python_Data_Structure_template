# Quick Sort
### Space complexity
inplace 
### Time complexity
Worst case -> O(n^2)
Avg. case -> O(nlog(n)
best case -> O(nlog(n))

```python
def quicksort(array, lower, upper):
    if lower < upper:
        pivot = partition(array, lower, upper)
        quicksort(array, lower, pivot-1)
        quicksort(array, pivot+1, upper)
    return

def partition(array, lower, upper):
    pivot = array[upper]
    entryIndex = currentIndex = lower 
    while currentIndex <= upper:
        if array[currentIndex] < pivot:
            swap(array, entryIndex, currentIndex)
            entryIndex += 1
        currentIndex += 1
    swap(array, entryIndex, upper)
    return entryIndex
def swap(array, A, B):
    temp = array[A]
    array[A] = array[B]
    array[B] = temp

quicksort(array, 0, len(array) - 1)
```
