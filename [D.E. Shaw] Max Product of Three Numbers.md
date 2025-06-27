# Problem: Maximum Product of Three Numbers

**Question:**  
Given a list of integers, return the **maximum product** of any **three numbers** in the array.

---

## Examples

**Example 1:**  
Input:  
`A = [1, 3, 4, 5]`  
Output:  
`60`  

**Explanation:**  
The maximum product is obtained by multiplying the top three numbers:  
`3 * 4 * 5 = 60`

---

**Example 2:**  
Input:  
`B = [-4, -2, 3, 5]`  
Output:  
`40`  

**Explanation:**  
The maximum product is obtained by multiplying the two smallest (most negative) numbers and the largest positive number:  
`-4 * -2 * 5 = 40`

---

## Constraints

- The input list contains at least **three integers**
- Elements can be **positive, negative, or zero**

---

## Hints

- Consider both the **three largest numbers** and the combination of **two smallest (negative) numbers** with the largest number.
- Sorting may help.

---
```python 

def max_three(nums):
    nums.sort()
    # Case 1: Product of the three largest numbers
    max1 = nums[-1] * nums[-2] * nums[-3]
    # Case 2: Product of two smallest (most negative) and the largest number
    max2 = nums[0] * nums[1] * nums[-1]
    
    return max(max1, max2)
