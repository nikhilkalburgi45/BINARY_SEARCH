# 3. Upper Bound in Sorted Array

## Problem Overview

Given a sorted array of integers `arr`, an integer `x`, and the size `n`, implement a function `upperBound` to find the smallest index where the value is greater than `x`. If no such value exists, return `n`.

- **Input:**
  - `arr = [1, 3, 5, 7, 9]`
  - `x = 5`
  - `n = 5`
- **Output:**

  - `3`

- **Explanation:**
  - The first element greater than `5` is `7`, which is at index `3`.

## Function Requirements

The function should:

1. Use two pointers: `low` and `high` to traverse the array.
2. Calculate the middle index (`mid`).
3. Compare `arr[mid]` with `x`.
4. If `arr[mid]` is greater than `x`, update `ans` with `mid` and move `high` to `mid - 1`.
5. If `arr[mid]` is less than or equal to `x`, move `low` to `mid + 1`.
6. Return the `ans` which contains the index of the upper bound.

## Solution: `upperBound` Function

```cpp
int upperBound(vector<int> &arr, int x, int n) {
    int low = 0, high = n - 1;
    int ans = n;  // Default answer is `n`, which is out of bounds

    while (low <= high) {
        int mid = (low + high) / 2;

        // If arr[mid] is greater than x, we have a potential answer
        if (arr[mid] > x) {
            ans = mid;  // Update answer to mid index
            high = mid - 1;  // Look for smaller index on the left
        } else {
            low = mid + 1;  // Otherwise, look on the right side
        }
    }

    return ans;  // Return the upper bound index
}

```

## Step-by-Step Breakdown

1. Initialize Variables:
   low = 0: The starting index of the array.
   high = n - 1: The ending index of the array.
   ans = n: A variable to store the upper bound index, initialized to n (out of bounds).

2. Loop Through the Array:
   Use a while (low <= high) loop to perform the binary search.

3. Calculate Mid Index:
   Compute the middle index as mid = (low + high) / 2.

4. Check Mid Element:
   If arr[mid] > x, update ans to mid and move high to mid - 1 to search for smaller valid indices on the left.
   If arr[mid] <= x, move low to mid + 1 to search on the right.

5. Return the Answer:
   After the loop, return ans, which will be the index of the smallest element greater than x. If no such element exists, it will return n.
   Complexity Analysis
   Time Complexity: O(log n)

## Complexity Analysis

1. time complexity.
2. Space Complexity: O(1)
