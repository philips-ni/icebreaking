# N Queens

## Problem Statement

Write an algorithm to print all ways of arranging N queeens on an NxN chess board so that none of them share the same row, column, diagonal. In this case, "diagonal" means all diagonals not just the two that bisect the board.

## Solution
Place queens row by row based on a DFS search concept

Check each column for all possible spots to place a queen

## Code

### Java
```java
public class NQueens{

	private static final int GRID_SIZE = 8;

	public static void placeQueens(int row, Integer[] columns, ArrayList<Integer[]> results) {
		if (row == GRID_SIZE) {
			results.add(columns.clone());
		} else {
			for (int col = 0; col < GRID_SIZE; col++) {
				if (checkValid(columns, row, col)) {
					columns[row] = col; // place queen
					placeQueens(row + 1, columns, results);
				}
			}
		}
	}

	private static boolean checkValid(Integer[] columns, int row, int column) {
		for (int row1 = 0; row1 < row; row1++) {
			int column1 = columns[row1];

			// check if there is a queen in the same column
			if (column1 == column)
				return false;

			// check if there is a queen in the diagonals
			int columnDistance = Math.abs(column1 - column);
			int rowDistance = Math.abs(row1 - row);

			if (columnDistance == rowDistance)
				return false;
		}

		return true;
	}

	public static void main(String[] args) {
		Integer[] columns = new Integer[GRID_SIZE];
		ArrayList<Integer[]> results = new ArrayList<Integer[]>();
		placeQueens(0, columns, results);
		for (int i = 0; i < results.size(); i++) {
			System.out.println(Arrays.toString(results.get(i)));
		}
	}
}
```

### Python

```
# filename: nqeens.py
class Solution(object):
    def solveNQueens(self, n):
        if n == 0:
            return []
        solutions = []
        self.dfs(n, [], solutions)
        # print solutions
        return self.convert(solutions)
    
    def dfs(self,n,placed_queens,solutions):
        # print placed_queens
        length = len(placed_queens)
        if length == n:
            # print "found it"
            solutions.append(placed_queens)
            return  # backtrack
        for i in range(0,n):
            if self.isAllowed(n, i,placed_queens):
                self.dfs(n,placed_queens + [i],solutions)
            else:
                pass # backtrack

    def isAllowed(self, n, i, placed_queens):
        length = len(placed_queens)
        for col, row in enumerate(placed_queens):
            if i == row:
                return False
            if abs(i-row) == abs(length - col):
                return False
        return True

    def convert(self,solutions):
        if len(solutions) == 0:
            return []
        out = []
        item_tpl = ["."] * len(solutions[0])
        for s in solutions:
            s_item = []
            for i in s:
                item = item_tpl[:]
                item[i] = "Q"
                s_item.append(''.join(item))
            out.append(s_item)
        return out

#filename: nqueens_test.py 
import unittest
import nqueens

class TestNqueens(unittest.TestCase):
    def test_solveNQueens(self):
        s = nqueens.Solution()
        expectedOut = [
            [".Q..",
             "...Q",
             "Q...",
             "..Q."],
            ["..Q.",
             "Q...",
             "...Q",
             ".Q.."]
        ]
        self.assertEqual(s.solveNQueens(4), expectedOut)
        self.assertEqual(s.solveNQueens(0), [])
        self.assertEqual(s.solveNQueens(1), [['Q']])
        self.assertEqual(s.solveNQueens(2), [])
        self.assertEqual(s.solveNQueens(3), [])        
if __name__ == '__main__':
    unittest.main()

```
## Time Space Complexity

O(n) = n * O(n-1) = n * (n-1) * O(n-2) = n * (n-1) * O(n-2)  * ... * 2 *  1 = n!

