# Two Sum in Sorted Array (Constant Space)

## Problem Statement

You are given an array of integers `nums` **sorted in non-decreasing order**, meaning that each value is equal to or greater than the one before it.

Return the **indices of the two values** in `nums` that **add up to a given target number**.

### Clarifications:

- There is at most **one solution**.
- If there is **no valid solution**, return `[-1, -1]`.
- Return the indices in **increasing order** (i.e. `[1,3]`, NOT `[3,1]`).
- Your solution must use **constant extra space**.
  - This means that the size of any objects you create **cannot grow** with the length of `nums`.

---

## Example #1

**Input:**

```python
nums = [1, 3, 4, 5, 7, 12, 15]
target = 9
```

**Output:**

```python
[2, 3]
```

**Explanation:** The values at indices 2 and 3 (4 and 5, respectively) add up to 9.

---

## Approach

Since the array is sorted, we can use a **two-pointer approach** to find the solution in O(n) time and O(1) space:

1. Initialize two pointers:
   - `left = 0`
   - `right = len(nums) - 1`
2. Repeat while `left < right`:
   - Calculate `current_sum = nums[left] + nums[right]`
   - If `current_sum == target`: return `[left, right]`
   - If `current_sum < target`: increment `left`
   - If `current_sum > target`: decrement `right`
3. If no pair is found, return `[-1, -1]`

---

## Python Implementation

```python
def two_sum_sorted(nums, target):
    left, right = 0, len(nums) - 1

    while left < right:
        current_sum = nums[left] + nums[right]

        if current_sum == target:
            return [left, right]
        elif current_sum < target:
            left += 1
        else:
            right -= 1

    return [-1, -1]
```

---

## Test Case

```python
nums = [1, 3, 4, 5, 7, 12, 15]
target = 9
print(two_sum_sorted(nums, target))  # Output: [2, 3]
```

---

## Space & Time Complexity

- **Time Complexity**: O(n)
- **Space Complexity**: O(1) (Constant extra space)

