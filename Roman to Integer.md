# 🏛️ Roman to Integer

## Problem Statement

Given a valid Roman numeral, convert it to an integer.

In case you don't think about the Roman empire that often, and need a crash course on how to go from Superbowl "XLIV" to an actual number, here's the table mapping the numerals to their values:

| Symbol | Value |
|--------|-------|
| I      | 1     |
| V      | 5     |
| X      | 10    |
| L      | 50    |
| C      | 100   |
| D      | 500   |
| M      | 1000  |

The numerals are generally written from largest to smallest from left to right. For example:

- **XI** → X (10) + I (1) = 11
- **XXX** → 10 + 10 + 10 = 30

However, in some cases, a smaller numeral comes **before** a larger one to indicate **subtraction**:

- **IV** = 4 (5 - 1)
- **XC** = 90 (100 - 10)
- **CM** = 900 (1000 - 100)

### Subtraction Rules:

- `I` comes before `V` (5) or `X` (10) → 4 and 9
- `X` comes before `L` (50) or `C` (100) → 40 and 90
- `C` comes before `D` (500) or `M` (1000) → 400 and 900

---

## Examples

**Example :**

Input: s = "XI"
Output: 11
Explanation: X = 10, I = 1, XI = 11

Input: s = "LXIX"
Output: 69
Explanation: L = 50, X = 10, IX = 9 → Total = 69. Nice.



```python


def roman_to_int(s: str) -> int:
    roman_map = {
        'I': 1,
        'V': 5,
        'X': 10,
        'L': 50,
        'C': 100,
        'D': 500,
        'M': 1000
    }
    
    total = 0
    prev_value = 0

    for char in reversed(s):
        current_value = roman_map[char]
        if current_value < prev_value:
            total -= current_value
        else:
            total += current_value
        prev_value = current_value

    return total

