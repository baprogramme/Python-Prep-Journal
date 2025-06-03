# Fizz Buzz Sum

Write a function `fizz_buzz_sum` to find the sum of all multiples of 3 or 5 below a target value.

## Problem Description

Given a target value `n`, return the sum of all numbers less than `n` that are divisible by either 3 or 5.

## Example

**Input:**
```
target = 10
```

**Multiples of 3 or 5 below 10:**
```
3, 5, 6, 9
```

**Output:**
```
3 + 5 + 6 + 9 = 23
```

So, the function should return:
```python
23
```

## Sample Python Code

```python
def fizz_buzz_sum(target):
    total = 0
    for i in range(target):
        if i % 3 == 0 or i % 5 == 0:
            total += i
    return total

#OR

def fizz_buzz_sum(target):
  A = [ 3*i for i in range(target+1) if target>3*i]
  B = [ 5*i for i in range(target+1) if target>5*i]
  
  A.extend(B)
  C = sum(set(A))

  return C


```
