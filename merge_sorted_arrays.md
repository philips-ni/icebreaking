# Merged Sorted Arrays

## Problem Statement

Given N sorted integer arrays, merged them into 1 single sorted array

## Solutions

### Solution 1
Type: [Heap](https://www.hackerearth.com/practice/notes/heaps-and-priority-queues/) classic usage

#### Analysis

Firstly, we will take the first item and its iterator of each arrays to initailize the heap.

Secondly, use "heappop" to take the top one(smallest one) out,
   - Append the item into the result
   - Use the returned iterator to find the next item, and "heappush" it into the heap

If the heap is not empty just repeat above steps, otherwise, the result would be the single sorted array.


#### Code

```python
# file: merged_sorted_arrays.py
import heapq
class Solution(object):
    def merged_sorted_array(self, sorted_arrays):
        min_heap = []
        sorted_arrays_iters = [iter(x) for x in sorted_arrays]

        for i, it in enumerate(sorted_arrays_iters):
            first_element = next(it,None)
            if first_element is not None:
                heapq.heappush(min_heap, (first_element, i))

        result = []
        while min_heap:
            smallest_entry, smallest_array_i = heapq.heappop(min_heap)
            smallest_array_iter = sorted_arrays_iters[smallest_array_i]
            result.append(smallest_entry)
            next_element = next(smallest_array_iter, None)
            if next_element is not None:
                heapq.heappush(min_heap, (next_element, smallest_array_i))
        return result
```

```python
# file: merged_sorted_arrays_test.py
import unittest
import merged_sorted_arrays

class TestMerged_Sorted_Arrays(unittest.TestCase):
    def test_merged_sorted_array(self):
        s = merged_sorted_arrays.Solution()
        self.assertEqual(s.merged_sorted_array([[1,3],[2,4,6],[5,7]]), [1,2,3,4,5,6,7])
        self.assertEqual(s.merged_sorted_array([[3,10],[2,4,6,100],[5,7]]), [2,3,4,5,6,7,10,100])        
if __name__ == '__main__':
    unittest.main()

```
#### Complexity

## See Also
You can put some related links here.
Or related advanced topics you want to discuss.
