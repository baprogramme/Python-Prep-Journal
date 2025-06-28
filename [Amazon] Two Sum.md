# Two Sum - Return Indices

## Problem Statement

Given a list of integers `nums`, and an integer `target`, return the **indices** of the two numbers which sum up to the target. **Do not use the same list element twice.**

### Clarifications:

- There is **at most one** solution.
- If there is **no valid solution**, return `[-1, -1]`.
- Return the indices in **increasing order** (i.e., `[1, 3]`, **NOT** `[3, 1]`).

---

## Examples

### Example 1

**Input:**

```
nums = [1, 4, 6, 10]  
target = 10
```

**Output:**

```
[1, 2]
```

**Explanation:**\
Because `4 + 6 == 10`, we return the index of elements 4 and 6, which is `[1, 2]`.

---

### Example 2

**Input:**

```
nums = [1, 4, 6, 10]  
target = 11
```

**Output:**

```
[0, 3]
```

**Explanation:**\
Because `nums[0] + nums[3] == 11`, we return `[0, 3]`.

---

### Example 3

**Input:**

```
nums = [1, 4, 6, 10]  
target = 2
```

**Output:**

```
[-1, -1]
```

**Explanation:**\
There are no two elements we can pick that sum up to 2.\
**Note:** You can't use the same element twice.

---


``` python

def two_sum_indices(nums, target):
    num_to_index = {}

    for i, num in enumerate(nums):
        complement = target - num
        if complement in num_to_index:
            return sorted([num_to_index[complement], i])
        num_to_index[num] = i

    return [-1, -1]

