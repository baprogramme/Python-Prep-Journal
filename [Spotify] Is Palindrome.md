# Palindrome Checker (In-Place, Memory-Efficient)

**Problem Statement:**

Given a string `phrase`, return `True` if it is a palindrome, otherwise return `False`.

A **palindrome** is a string that reads the same forward and backward. The check is **case-insensitive** and **ignores all non-alphanumeric characters**.

**Challenge:**  
Try solving this without using extra memory. Specifically, solve it **without making a copy of `phrase`**.

---

### Clarifications:

- `phrase` contains only: letters, numbers, spaces, and standard punctuation/symbols.
- Do not use additional strings or arrays for cleanup or reversed comparison.

---

### Examples

**Example 1:**

**Input:**  
`phrase = "Taco cat."`

**Output:**  
`True`

**Explanation:**  
Considering only alphanumeric characters and converting to lowercase, the string becomes `"tacocat"` which is a palindrome.

---

**Example 2:**

**Input:**  
`phrase = "I love SQL <3"`

**Output:**  
`False`

**Explanation:**  
After filtering and lowercasing, the string becomes `"ilovesql3"`, which is **not** a palindrome.

---

### Constraints

- Focus on in-place comparison using two pointers.
- Avoid extra space usage for string manipulation.

```python

def isPalindrome(phrase):
    left, right = 0, len(phrase) - 1

    while left < right:
        # Skip non-alphanumeric characters
        while left < right and not phrase[left].isalnum():
            left += 1
        while left < right and not phrase[right].isalnum():
            right -= 1

        # Compare characters ignoring case
        if phrase[left].lower() != phrase[right].lower():
            return False

        left += 1
        right -= 1

    return True

