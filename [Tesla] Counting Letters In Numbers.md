# Number Letter Counts

## Problem Statement

If the numbers from 1 to N are written out in words (e.g., "one", "two", "three", "four", etc.), how many letters are used in total when writing all numbers between 1 and N (inclusive)?

### Rules:

- **Do not count** spaces or hyphens.
- **British usage** applies (we're fancy like that): for numbers over 100, include "and" (e.g., "one hundred and fifteen").
- You can assume that `N` will always be **less than or equal to 1000**.

Given an integer `N`, return the total number of letters used when writing the numbers from 1 to `N` in words.

---

## Example

### Input:
N = 5
### Output: 
19


### Explanation:

The numbers between 1 and 5 written in words are:

- 1 → `"one"` (3 letters)
- 2 → `"two"` (3 letters)
- 3 → `"three"` (5 letters)
- 4 → `"four"` (4 letters)
- 5 → `"five"` (4 letters)

In total:  
`3 + 3 + 5 + 4 + 4 = 19 letters`

---


```python

def number_to_words(n):
    ones = ["", "one", "two", "three", "four", "five", "six", "seven",
            "eight", "nine", "ten", "eleven", "twelve", "thirteen",
            "fourteen", "fifteen", "sixteen", "seventeen", "eighteen", "nineteen"]

    tens = ["", "", "twenty", "thirty", "forty", "fifty",
            "sixty", "seventy", "eighty", "ninety"]

    if 1 <= n < 20:
        return ones[n]
    elif 20 <= n < 100:
        return tens[n // 10] + (ones[n % 10] if n % 10 != 0 else "")
    elif 100 <= n < 1000:
        if n % 100 == 0:
            return ones[n // 100] + "hundred"
        else:
            return ones[n // 100] + "hundredand" + number_to_words(n % 100)
    elif n == 1000:
        return "onethousand"
    else:
        return ""

def total_letter_count(N):
    total = 0
    for i in range(1, N + 1):
        word = number_to_words(i)
        total += len(word)
    return total



