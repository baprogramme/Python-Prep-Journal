# Convert Integer to Base 13

## Problem Statement

Given an integer `num`, return its string representation in **base 13**.

In case you don’t use base 13 that much (who does, right?), here’s a quick rundown:

- Just like base 10 uses digits from `0` to `9`, base 13 uses:
  - `0-9` for values 0 through 9
  - `A` for 10
  - `B` for 11
  - `C` for 12

---

## Base 13 Conversion Examples

| Decimal | Base 13 |
|---------|---------|
| 9       | "9"     |
| 10      | "A"     |
| 11      | "B"     |
| 12      | "C"     |
| 13      | "10"    |
| 14      | "11"    |
| 49      | "3A"    | <!-- 3 * 13 + 10 = 49 -->
| 69      | "54"    | <!-- 5 * 13 + 4 = 69 -->

---

## Explanation

To convert a number to base 13:

1. Repeatedly divide the number by 13.
2. Record the remainder each time.
3. Use `0-9` and `A-C` to represent remainders.
4. Build the result string from last remainder to first.

---

Let me know if you'd like the code to implement this in Python or any other language!


``` python


def to_base13(num):
    if num == 0:
        return "0"
    
    digits = "0123456789ABC"
    result = ""
    negative = num < 0
    
    num = abs(num)
    
    while num > 0:
        remainder = num % 13
        result = digits[remainder] + result
        num //= 13
    
    if negative:
        result = "-" + result
    
    return result

