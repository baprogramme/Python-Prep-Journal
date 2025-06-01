# Problem: Digital Clone of DJ Khaled

We're trying to create a digital clone of DJ Khaled. No fancy AI or algorithms needed.

Just take a number and add another one:

---

## Problem Description

You are given an integer array `digits`, where each `digits[i]` is the i-th digit of a positive whole number. It is ordered from the most significant to the least significant digit.

Your task is to return an array of digits of the number **after adding another one** to the input.

---

## Examples

### Example 1

**Input:**  
`digits = [1, 2, 3]`

**Output:**  
`[1, 2, 4]`

---

### Example 2

**Input:**  
`digits = [6, 9]`

**Output:**  
`[7, 0]`

---

## Notes

- The input array always represents a positive integer.
- After adding one to the number represented by the input digits, the output should be in the same format: a list of digits, ordered from most significant to least significant.

``` python

def another_one(digits):
    # Start from the last digit (rightmost digit)
    n = len(digits)
    for i in range(n-1, -1, -1):
        # Add 1 to the current digit
        digits[i] += 1
        if digits[i] < 10:
            # No carry, so we can return immediately
            return digits
        else:
            # If it's 10, set current digit to 0 and carry over to next
            digits[i] = 0
    
    # If we exited the loop, there was a carry at the most significant digit
    # e.g., 999 -> 1000
    return [1] + digits


