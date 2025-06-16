
# 🌀 Rotate Image by 90 Degrees Clockwise

You are given an **n x n 2D matrix** representing an image, and you need to rotate the image by **90 degrees clockwise**.

You are basically being asked to implement the functionality of:

```python
numpy.rot90(matrix, k=-1)
```

> ❗ **Note:** You must not use any helper libraries like NumPy.

---

## ✅ Example #1

**Input:**

```python
matrix = [[5, 1],
          [6, 2]]
```

**Output:**

```python
[[6, 5],
 [2, 1]]
```

---

## ✅ Example #2

**Input:**

```python
matrix = [[3, 6, 9],
          [2, 5, 8],
          [1, 4, 7]]
```

**Output:**

```python
[[1, 2, 3],
 [4, 5, 6],
 [7, 8, 9]]
```

---



```python
def rotate_new_matrix(matrix):
    n = len(matrix)
    rotated = [[0] * n for _ in range(n)]

    for i in range(n):
        for j in range(n):
            rotated[j][n - 1 - i] = matrix[i][j]

    return rotated
```
