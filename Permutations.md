# Permutations

## Problem Statement

Write a function that returns all permutations of a given Integer list.

## Solution

Start with every single Integer in the list

Construct permutation with DFS search strategy

## Code

```java
pulic class Permutation{
	
	public static ArrayList<ArrayList<Integer>> listPermutation(int[] nums) {
		ArrayList<ArrayList<Integer>> results = new ArrayList<ArrayList<Integer>>();
		ArrayList<Integer> temp = new ArrayList<Integer>();
		permute(nums, temp, results);
		return results;
	}

	@SuppressWarnings("unchecked")
	private static void permute(int[] nums, ArrayList<Integer> temp, ArrayList<ArrayList<Integer>> results) {
		if (temp.size() == nums.length) {
			System.out.println(temp);
			results.add((ArrayList<Integer>)temp.clone());
		}

		for (int i = 0; i < nums.length; i++) {
			if (!temp.contains(nums[i])) {
				temp.add(nums[i]);
				permute(nums, temp, results);
				temp.remove(temp.size() - 1);
			}
		}
	}

	public static void main(String[] args) {
		int[] list = { 1, 2, 3 };
		listPermutation(list);
	}
}
```
## Time Space Complexity

O(n) = n * O(n-1) = n!
