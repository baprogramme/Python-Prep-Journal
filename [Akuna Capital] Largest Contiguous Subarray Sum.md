# Maximum Contiguous Subarray Sum

## 🧾 Problem Statement

"Given an integer array, find the sum of the largest contiguous subarray within the array.

For example, if the input is `[-1, -3, 5, -4, 3, -6, 9, 2]`, then return `11` (because of `[9, 2]`).

Note that if all the elements are negative, you should return `0`."

---

## 🔍 Explanation

This is a classic dynamic programming problem known as **Kadane’s Algorithm**.

The idea is to iterate through the array, and at each step, keep track of:
- `current_sum`: maximum subarray sum ending at the current index
- `max_sum`: overall maximum sum seen so far

If all numbers are negative, the result is `0` (i.e., an empty subarray contributes the maximum sum).

---

## ✅ Constraints

- Input: List of integers (can include both positive and negative numbers)
- Output: An integer representing the sum of the maximum contiguous subarray

---

## 💡 Example

### Input:

arr = [-1, -3, 5, -4, 3, -6, 9, 2]


### Output

11  # from subarray [9, 2]



```python

def max_subarray_sum(arr):
    max_sum = 0
    current_sum = 0

    for num in arr:
        current_sum = max(0, current_sum + num)
        max_sum = max(max_sum, current_sum)

    return max_sum

