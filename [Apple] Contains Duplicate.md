# Contains Duplicate Checker

## Problem Statement

Given a list of integers called `input`, return `True` if any value appears at least twice in the array. Return `False` if every element in the input list is distinct.

## Examples

### Example 1:
**Input:**  
`[1, 3, 5, 7, 1]`  
**Output:**  
`True`  
**Explanation:**  
The number `1` appears twice in the list.

### Example 2:
**Input:**  
`[1, 3, 5, 7]`  
**Output:**  
`False`  
**Explanation:**  
All elements in the list are unique.

## Constraints
- The input is a list of integers.
- The function should return a boolean value (`True` or `False`).

## Sample Code
```python
def contains_duplicate(nums) -> bool:
    seen = set()
    for num in nums:
        if num in seen:
            return True
        seen.add(num)
    return False

#OR

def contains_duplicate(nums) -> bool:
    return len(nums) != len(set(nums))




