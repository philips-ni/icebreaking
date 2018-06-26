# GRAY CODE
## Problem Statement
The gray code is a binary numeral system where two successive values differ in only one bit.

Given a non-negative integer n representing the total number of bits in the code, print the sequence of gray code. A gray code sequence must begin with 0.

For example, given n = 2, return [0,1,3,2]. Its gray code sequence is:
```
00 - 0
01 - 1
11 - 3
10 - 2
```

Note:
 - For a given n, a gray code sequence is not uniquely defined.
```
For example, [0,2,3,1] is also a valid gray code sequence according to the above definition.
```

## Solution

If we look into the example, we will get the idea, if we can get to know gray_code(n-1), the first part of answer could be exactly gray_code(n-1), and the seond part is revered(gray_code(n-1) with the highest big set to 1.

for example: for n = 3:
gray_code(n-1) is equal to [00,01,11,10]
gray_code(n) is equal to [000,001,011,010,110,111,101,100]

The key point is the end of the first part is 010, and start of the second part is 110.

## Code
```python
# filename: gray_code.py
class Solution(object):
    def grayCode(self, n):
        if n == 0:
            return [0]
        if n == 1:
            return [0,1]
        tmp = self.grayCode(n-1)
        reverseTmp = tmp[::-1]
        newPart = [x + pow(2, n - 1) for x in reverseTmp]
        return tmp + newPart

# filename:gray_code_test.py
import unittest
import gray_code

class TestGray_Code(unittest.TestCase):
    def test_grayCode(self):
        s = gray_code.Solution()
        self.assertEqual(s.grayCode(0), [])        
        self.assertEqual(s.grayCode(1), [0,1])
        self.assertEqual(s.grayCode(2), [0,1,3,2])
        self.assertEqual(s.grayCode(3), [0,1,3,2,6,7,5,4])                
        
if __name__ == '__main__':
    unittest.main()
```
## Complexity 
TBD
