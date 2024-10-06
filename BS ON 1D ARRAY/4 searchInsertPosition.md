# 5. Search Insert Position in Sorted Array

## Problem Overview

Given a sorted array of integers `arr` and an integer `x`, implement a function `searchInsert` to find the index where `x` should be inserted to maintain the sorted order. If `x` already exists in the array, return its index.

- **Input:**

  - `arr = [1, 3, 5, 6]`
  - `x = 5`

- **Output:**

  - `2`

- **Explanation:**
  - The target `5` is found at index `2`. If `x` were not in the array, return the index where it would be inserted.

## Function Requirements

The function should:

1. Use binary search with two pointers: `low` and `high`.
2. Calculate the middle index (`mid`).
3. If the element at `mid` is greater than or equal to `x`, update the possible answer `ans` to `mid` and move `high` to `mid - 1` to search for smaller valid indices on the left.
4. If the element at `mid` is less than `x`, move `low` to `mid + 1` to search on the right.
5. Return the value of `ans` as the insertion point or the index of `x` if it exists.

## Solution: `searchInsert` Function

```cpp
int searchInsert(vector<int>& arr, int x) {
    int n = arr.size();  // Get the size of the array
    int low = 0, high = n - 1;  // Initialize two pointers for binary search
    int ans = n;  // Default answer is `n`, which is the array size (out of bounds)

    // Perform binary search:
    while (low <= high) {
        int mid = (low + high) / 2;  // Calculate the middle index

        // If the middle element is greater than or equal to `x`,
        // update the possible insertion index and search on the left side
        if (arr[mid] >= x) {
            ans = mid
        // If the middle element is less than `x`, move the low pointer to the right
        else {
            low = mid + 1;  // Search on the right side
        }
    }

    // Return the index where `x` should be inserted
    return ans;  // If `x` is already present, return its index; otherwise, return the insertion point
}

```

## Step-by-Step Breakdown

1. Initialize Variables:
   low = 0: Starting index of the array.
   high = n - 1: Ending index of the array (where n is the size of the array).
   ans = n: Default answer, assuming x should be inserted at the end.

2. Loop Through the Array:
   Use a while loop with the condition low <= high to continue the search until the pointers converge.

3. Calculate Mid Index:
   Compute the mid index as mid = (low + high) / 2.

4. Compare Mid Element:
   If arr[mid] >= x, update ans to mid and search on the left by setting high = mid - 1.
   If arr[mid] < x, search on the right by setting low = mid + 1.

5. Return Result:
   Once the loop ends, return ans, which indicates the index where x should be inserted or where it is found.

## Complexity Analysis

1. Time Complexity: O(log n)
   The algorithm efficiently reduces the search space by half in each iteration, leading to logarithmic time complexity.
2. Space Complexity: O(1)
   The function uses a constant amount of extra space for the low, high, mid, and ans variables.
