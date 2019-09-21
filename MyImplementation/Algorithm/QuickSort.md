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
    i = j = lower 
    while j <= upper:
        if array[j] < pivot:
            swap(array, i, j)
            i += 1
        j += 1
    swap(array, i, upper)
    return i
def swap(array, A, B):
    temp = array[A]
    array[A] = array[B]
    array[B] = temp

quicksort(array, 0, len(array) - 1)
```
