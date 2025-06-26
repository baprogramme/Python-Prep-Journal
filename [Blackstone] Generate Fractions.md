# Simplified Fractions Generator

## Problem Statement

Given an integer `n`, generate **all simplified fractions** between 0 and 1 (exclusive), where the **denominator is less than or equal to `n`**.

A fraction is **simplified** if the numerator and denominator have **no common divisors other than 1** (i.e., their GCD is 1).

Return a **sorted list** of fractions, where each fraction is represented as `[numerator, denominator]`.

---

## Examples

### Example 1

**Input:**
n = 3

**Output:**
[[1, 2], [1, 3], [2, 3]]


---

### Example 2

**Input:**
n = 4


**Output:**

[[1, 2], [1, 3], [1, 4], [2, 3], [3, 4]]


---

### Example 3

**Input:**

n = 5


**Output:**


[[1, 2], [1, 3], [1, 4], [1, 5], [2, 3], [2, 5], [3, 4], [3, 5], [4, 5]]


---

## Constraints

- `1 <= n <= 100`

---

## Approach

1. Iterate over all denominators from 2 to `n`.
2. For each denominator `d`, iterate over numerators `1` to `d-1`.
3. For each pair `[numerator, denominator]`, check if `gcd(numerator, denominator) == 1`.
4. If yes, the fraction is simplified and is added to the result list.
5. Sort the resulting list by the actual floating-point value of the fraction: `numerator / denominator`.

---

## Python Solution

```python
from math import gcd

def simplified_fractions(n):
    result = []
    for denom in range(2, n + 1):
        for num in range(1, denom):
            if gcd(num, denom) == 1:
                result.append([num, denom])
    result.sort()  # Lexicographic sort by default
    return result
