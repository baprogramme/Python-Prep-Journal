# Anagram Checker

## Problem Statement

Given two strings `s` and `t`, return `True` if the two strings are **anagrams** of each other, otherwise return `False`.

An **anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, using **all the original letters exactly once**.

You can assume both strings contain **only lowercase alphabet characters**.

---

## Examples

### Example 1

**Input:**  
`s = "listen"`  
`t = "silent"`  

**Output:**  
`True`  

---

### Example 2

**Input:**  
`s = "astronomer"`  
`t = "moonstarer"`  

**Output:**  
`True`  

---

### Example 3

**Input:**  
`s = "lemur"`  
`t = "lemer"`  

**Output:**  
`False`  

---

## Approach

To check whether two strings are anagrams:

1. Check if their lengths are the same.
2. Sort both strings and compare them.
   - If they match, they are anagrams.
   - If not, they are not.

Alternatively, you can use a frequency counter (like a dictionary or `collections.Counter`) to compare character counts.

---

## Python Code

```python
def is_anagram(s: str, t: str) -> bool:
    return sorted(s) == sorted(t)

#OR

def is_anagram(s, t):
  return (set(s)==set(t))
