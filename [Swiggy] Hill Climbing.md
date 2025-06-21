# Hill Climbing Steps Problem

You're attempting to climb a hill—not in a mathematical optimization sense (check out hill climbing for that), but literally outside, touching grass, and trying to climb a hill.

Imagine there are `n` steps carved into the hill. You can go up using either **1 or 2 steps at a time**.

Your task is to **return the number of distinct ways to reach the top of the hill**.

---

## Example 1

**Input:**  
`3`

**Output:**  
`3`

**Explanation:**  
There are three distinct ways to climb to the top of a hill with 3 steps:
1. Take 1 step, then 1 step, then 1 step.
2. Take 1 step, then 2 steps.
3. Take 2 steps, then 1 step.

---

## Example 2

**Input:**  
`4`

**Output:**  
`5`

**Explanation:**  
There are five distinct ways to climb to the top of a hill with 4 steps:
1. Take 1 step, then 1 step, then 1 step, then 1 step.
2. Take 1 step, then 1 step, then 2 steps.
3. Take 1 step, then 2 steps, then 1 step.
4. Take 2 steps, then 1 step, then 1 step.
5. Take 2 steps, then 2 steps.

---

## Constraints

- `1 <= n <= 45`

---

## Hint

This is a classic **dynamic programming** problem. The number of ways to climb `n` steps is the sum of the ways to climb `n - 1` steps and `n - 2` steps, just like the Fibonacci sequence.


```python

def climb_stairs(n):
    if n <= 2:
        return n
    first, second = 1, 2
    for _ in range(3, n + 1):
        first, second = second, first + second
    return second

