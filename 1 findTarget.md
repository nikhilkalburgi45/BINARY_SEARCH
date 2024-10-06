# 1. Binary Search to find target in sorted array

## Problem Overview

Given a sorted array of integers `nums` and an integer `target`, implement binary search to find the index of the `target`. If the target is not found, return `-1`.

- **Input:**
  - `nums = [1, 3, 5, 7, 9]`
  - `target = 5`
- **Output:**
  - `2`
- **Explanation:**
  - The target `5` is found at index `2`.

## Function Requirements

The function should:

1. Divide the array into halves using two pointers: `low` and `high`.
2. Compute the middle index (`mid`).
3. Compare the middle element `nums[mid]` with the target.
4. If the middle element equals the target, return the index `mid`.
5. If the target is greater than the middle element, discard the left half by setting `low = mid + 1`.
6. If the target is smaller than the middle element, discard the right half by setting `high = mid - 1`.
7. If the target is not found, return `-1`.

## Solution: `binarySearch` Function

```cpp
int binarySearch(vector<int>& nums, int target) {
    int n = nums.size();  // Size of the array
    int low = 0, high = n - 1;

    // Perform binary search:
    while (low <= high) {
        int mid = (low + high) / 2;  // Calculate the mid index

        // Check if the middle element is the target
        if (nums[mid] == target) return mid;

        // If the target is greater than the mid element, discard the left half
        else if (target > nums[mid]) low = mid + 1;

        // If the target is smaller than the mid element, discard the right half
        else high = mid - 1;
    }

    // Return -1 if the target is not found
    return -1;
}

```

Step-by-Step Breakdown

1. Initialize Variables:
   low = 0: Starting index of the array.
   high = n - 1: Ending index of the array (where n is the size of the array).

2. Loop Through the Array:
   Use a while loop with the condition low <= high to keep dividing the array.

3. Calculate Mid Index:
   Compute the mid index as mid = (low + high) / 2. 4. Compare Mid Element:
   If nums[mid] == target, return mid because the target is found.
   If target > nums[mid], move the low pointer to the right by setting low = mid + 1.
   If target < nums[mid], move the high pointer to the left by setting high = mid - 1.

4. Return Result:
   If the loop ends without finding the target, return -1 indicating the target is not present in the array.

Complexity Analysis :-
Time Complexity: O(log n)
In each iteration, we reduce the search space by half, making binary search logarithmic in time complexity.

Space Complexity: O(1)
Only a constant amount of extra space is used for the low, high, and mid variables.
