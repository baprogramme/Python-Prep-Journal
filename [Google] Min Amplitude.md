# Minimum Amplitude After Changing up to 3 Elements

## Problem Statement

Given an integer array `arr`, the **amplitude** is defined as the **difference between the largest and smallest** values in the array.

You are allowed to **change up to three elements** in the array to **any value**.

Return the **minimum possible amplitude** that can be achieved after performing up to 3 such changes.

---

## Examples

### Example 1:

**Input:**
```python
arr = [4, -8, -1, 3, 7, 10, 5]

```

**Output:**

4

**Explanation:**

We can make the following changes:

Change -8 and -1 to 3

Change 10 to 7

Resulting array: [4, 3, 3, 3, 7, 7, 5]

New amplitude = 7 - 3 = 4

### Example 2:

**Input:**

arr = [3, 5, 10, 0]


**Output:**

0

**Explanation:**

We can change 3, 5, and 10 to 0.

Resulting array: [0, 0, 0, 0]

New amplitude = 0 - 0 = 0


```python

def min_amplitude(arr):
    n = len(arr)
    if n <= 4:
        return 0  # We can make all elements equal

    arr.sort()
    # Try 4 possibilities of removing up to 3 elements
    return min(
        arr[-1 - i] - arr[3 - i] for i in range(4)
    )
