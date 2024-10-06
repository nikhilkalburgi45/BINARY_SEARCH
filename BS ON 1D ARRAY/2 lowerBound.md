# 2. Lower Bound in a Sorted Array

## Problem Overview

Given a sorted array of integers `arr` and an integer `x`, implement a function to find the **lower bound** of `x` in the array. The lower bound is the index of the first element that is **greater than or equal to** `x`. If no such element exists, return the size of the array `n`.

- **Input:**
  - `arr = [1, 3, 3, 5, 7]`
  - `x = 3`
- **Output:**
  - `1`
- **Explanation:**
  - The first position where 3 can be inserted is at index 1.

## Function Requirements

The function should:

1. Use binary search to efficiently find the lower bound.
2. Return the index of the first element that is greater than or equal to `x`.
3. If no such element exists, return the size of the array `n`.

## Solution: `lowerBound` Function

```cpp
int lowerBound(vector<int> arr, int n, int x) {
    int low = 0, high = n - 1;
    int ans = n;  // Initialize the answer to n (which means x is larger than all elements)

    // Perform binary search:
    while (low <= high) {
        int mid = (low + high) / 2;

        // If arr[mid] is a possible lower bound
        if (arr[mid] >= x) {
            ans = mid;      // Update the answer to current mid
            high = mid - 1; // Search the left side for a potentially smaller index
        } else {
            low = mid + 1;  // Search the right side if arr[mid] < x
        }
    }

    return ans;  // Return the final answer
}

```

## Step-by-Step Breakdown

1. Initialize Variables:
   low = 0: The start of the search space.
   high = n - 1: The end of the search space.
   ans = n: This is the default answer, meaning no element greater than or equal to x is found.

2. Binary Search:
   In each step, calculate the mid index using (low + high) / 2.
   If arr[mid] is greater than or equal to x, it could be the lower bound, so store mid in ans and move high to mid - 1 to search for a lower index.
   If arr[mid] is less than x, move low to mid + 1 to search the right side.

3. Return Result: After the binary search loop, return ans, which holds the index of the lower bound.

## Complexity Analysis

1. Time Complexity:
   O(log n) where n is the number of elements in the array, because the search space is halved in each step of the binary search.
2. Space Complexity:
   O(1), as only a few extra variables (low, high, mid, and ans) are used.
