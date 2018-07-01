# Quick Sort

## Problem Statement
Quicksort is a divide and conquer algorithm. Quicksort first divides a large array into two smaller sub-arrays: the low elements and the high elements. Quicksort can then recursively sort the sub-arrays.

The steps are:
 - Pick an element, called a pivot, from the array.
 - Partitioning: reorder the array so that all elements with values less than the pivot come before the pivot, while all elements with values greater than the pivot come after it (equal values can go either way). After this partitioning, the pivot is in its final position. This is called the partition operation.
Recursively apply the above steps to the sub-array of elements with smaller values and separately to the sub-array of elements with greater values.


## Solutions


### Solution 1
Type: Recursion

The recursion part is trival, partition part is a little tricky, the idea is :
  - set the first item as pivot
  - use 2 pointer, i from left to right, j from right to left.
  - from each round, from left to right, find the first item which is bigger than pivot, from right to left, find the first item which is less than pivot, and swap them ,
  
#### Code (Python)


```python
#filename: quick_sort.py 
class Solution(object):
    def quick_sort(self, l):
        if len(l) < 2:
            return
        else:
            self._quick_sort(l, 0, len(l) - 1)

    def _quick_sort(self,l, start, end):
        if start < end:
            pos = self.partition(l,start, end)
            self._quick_sort(l,start,pos-1)
            self._quick_sort(l,pos+1, end)


    def partition(self, l, start, end):
        pivot = l[start]
        i, j = start-1, end+1
        while True:
            i += 1
            j -= 1
            while(l[i] < pivot): i+= 1
            while(l[j] > pivot ): j-= 1
            if i >= j: 
                return j
            l[i], l[j] = l[j], l[i]
```

```python
#file_name: quick_sort_test.py
import unittest
import quick_sort

class TestQuick_Sort(unittest.TestCase):
    def test_quick_sort(self):
        s = quick_sort.Solution()
        l = [1,3,2,4]
        s.quick_sort(l)
        self.assertEqual(l,[1,2,3,4])
        l = [1]
        s.quick_sort(l)
        self.assertEqual(l,[1])
        
if __name__ == '__main__':
    unittest.main()

```

#### Complexity

## See Also
You can put some related links here.
Or related advanced topics you want to discuss.

