# Looping Number Checker

## Problem Statement

Given an integer `n`, check if it is a **looping number**. A looping number has the following properties:

- It is repeatedly replaced by the **sum of the squares of its digits**.
- This process continues until:
  - The number becomes `1`, in which case it is **not** a looping number.
  - The number starts **repeating in a cycle** that does not include `1`, making it a **looping number**.

**Return `True` if `n` is a looping number, otherwise return `False`.**

---

## Example 1

**Input:**  
`n = 4`

**Output:**  
`True`

**Explanation:**

4² = 16
1² + 6² = 1 + 36 = 37
3² + 7² = 9 + 49 = 58
5² + 8² = 25 + 64 = 89
8² + 9² = 64 + 81 = 145
1² + 4² + 5² = 1 + 16 + 25 = 42
4² + 2² = 16 + 4 = 20
2² + 0² = 4 + 0 = 4

Since the number loops back to `4`, it is a **looping number**.

---

## Example 2

**Input:**  
`n = 19`

**Output:**  
`False`

**Explanation:**
1² + 9² = 1 + 81 = 82
8² + 2² = 64 + 4 = 68
6² + 8² = 36 + 64 = 100
1² + 0² + 0² = 1 + 0 + 0 = 1

Since the number reaches `1`, it is **not** a looping number.

``` python

def is_looping_number(n):
    seen = set()
    
    def sum_of_squares(num):
        return sum(int(digit)**2 for digit in str(num))
    
    while n != 1:
        if n in seen:
            return True  # Loop detected
        seen.add(n)
        n = sum_of_squares(n)
    
    return False  # Reached 1, so it's not a looping number
