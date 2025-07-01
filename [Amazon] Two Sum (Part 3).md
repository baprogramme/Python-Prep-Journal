# Maximum Pair Sum Less Than K

## Problem Statement

Given an array of integers `nums` and an integer `k`, return the **largest possible maxSum < k** such that:

- `maxSum = nums[i] + nums[j]`
- `i ≠ j`

If no such pair exists, return `-1`.

---

## Example #1

**Input:**

```python
nums = [34, 23, 1, 24, 75, 33, 54, 8]
k = 60
```

**Output:**

```python
58
```

**Explanation:** The greatest possible sum less than 60 is 58, made by adding `34 + 24`.

---

## Approach

1. Initialize `max_sum = -1`.
2. Loop through all possible pairs `(i, j)` with `i < j`.
3. For each pair, calculate the sum:
   - If `nums[i] + nums[j] < k`, update `max_sum` if this sum is greater than current `max_sum`.
4. Return `max_sum` after checking all pairs.

---

## Python Implementation

```python
def two_sum_less_than_k(nums, k):
    max_sum = -1
    n = len(nums)

    for i in range(n):
        for j in range(i + 1, n):
            s = nums[i] + nums[j]
            if s < k:
                max_sum = max(max_sum, s)

    return max_sum
```


## Time and Space Complexity

- **Time Complexity:** O(n^2), where n is the number of elements in the array
- **Space Complexity:** O(1), uses constant space

