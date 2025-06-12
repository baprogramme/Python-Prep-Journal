# Longest Consecutive Sequence

**Problem Statement:**

Given an array of integers `nums`, return the length of the longest consecutive sequence of elements that can be formed from the array.

A **consecutive sequence** consists of elements where each element is exactly 1 greater than the previous element. The elements in the sequence can be selected from any position in the array and do not need to appear in their original order.

---

## Examples

### Example 1
**Input:**  
`nums = [100, 4, 200, 1, 3, 2]`  
**Output:**  
`4`  
**Explanation:**  
The longest consecutive sequence is `[1, 2, 3, 4]`, which has a length of 4.

---

### Example 2
**Input:**  
`nums = [3, 2]`  
**Output:**  
`2`  
**Explanation:**  
The longest consecutive sequence is `[2, 3]`, which has a length of 2.

---

## Constraints

- The array may contain duplicates.
- The array can be unsorted.
- The sequence can start at any number in the array and must increment by 1.

---

```python 

def longest_consecutive(nums):
    max_counter= 1
    counter = 1
    num = sorted(set(nums))
    for i in range(1, len(num)):

        if num[i] == num[i - 1] +1:
            counter +=1
        else:
            max_counter = max(max_counter,counter)
            counter = 1
        # print(i)
    return max(max_counter, counter)
