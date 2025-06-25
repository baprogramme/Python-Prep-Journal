# Top N Frequent Elements

## Problem Statement

Given an integer array and an integer `n` as input, return the top `n` integers in the array (the ones that appear most frequently).  
Return the output in non-decreasing order.  
The test cases are generated in such a way that there will be a unique answer.

---

## Example #1

**Input:**  
`nums = [2, 1, 2, 3, 2, 1, 2, 1, 3, 4]`  
`n = 3`

**Output:**  
`[1, 2, 3]`

**Explanation:**  
The most frequent elements are:  
- 2 with a frequency of 4  
- 1 with a frequency of 3  
- 3 with a frequency of 2  

Finally, the output is sorted in non-decreasing order.

---

## Example #2

**Input:**  
`nums = [3, 2]`  
`n = 2`

**Output:**  
`[2, 3]`

---
```python

from collections import Counter

def top_n_frequent(nums, n):
    freq = Counter(nums)  # Step 1
    top_n = sorted(freq.items(), key=lambda x: -x[1])[:n]  # Step 2 & 3
    result = sorted([num for num, count in top_n])  # Step 4
    return result
