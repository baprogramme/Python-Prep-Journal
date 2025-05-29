# Matrix Diagonal Stripes Checker

You are given an m x n matrix. Your task is to determine if the matrix has diagonal stripes where all elements in each diagonal from top-left to bottom-right are of the same stripe—that is, they are identical.

In this context, each diagonal stripe runs from the top-left corner to the bottom-right corner of the matrix. Check if every diagonal stripe consists entirely of the same number.

Return **True** if all diagonal stripes are of the same stripe, otherwise return **False**.

---

### Example #1

Same Stripe DataLemur Example 1

**Input:**
```
matrix = [
  [42, 7, 13, 99],
  [6, 42, 7, 13],
  [1, 6, 42, 7]
]
```

**Output:**
```
True
```

**Explanation:**

In this grid, the diagonals are:

- `[1]`
- `[6, 6]`
- `[42, 42, 42]`
- `[7, 7, 7]`
- `[13, 13]`
- `[99]`

All elements in each diagonal are identical. Thus, the answer is **True**.

---

### Example #2

**Input:**
```
matrix = [
  [8, 23],
  [69, 1]
]
```

**Output:**
```
False
```

**Explanation:**

The diagonal `[8, 1]` does not consist of elements of the same stripe. Therefore, the answer is **False**.


``` python

def is_same_stripes(matrix):
    rows, cols = len(matrix), len(matrix[0])

    # Check diagonals starting from first row
    for col in range(cols):
        diagonal = [matrix[i][col + i] for i in range(min(rows, cols - col))]
        if len(set(diagonal)) != 1:
            return False

    # Check diagonals starting from first column (excluding [0][0])
    for row in range(1, rows):
        diagonal = [matrix[row + i][i] for i in range(min(rows - row, cols))]
        if len(set(diagonal)) != 1:
            return False

    return True

