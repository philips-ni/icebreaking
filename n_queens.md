# N Queens

## Problem Statement

Write an algorithm to print all ways of arranging N queeens on an NxN chess board so that none of them share the same row, column, diagonal. In this case, "diagonal" means all diagonals not just the two that bisect the board.

## Solution
Place queens row by row based on a DFS search concept

Check each column for all possible spots to place a queen

## Code

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
## Time Space Complexity

O(n) = n * O(n-1) = n * (n-1) * O(n-2) = n * (n-1) * O(n-2)  * ... * 2 *  1 = n!

