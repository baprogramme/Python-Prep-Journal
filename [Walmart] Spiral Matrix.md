# Spiral Matrix

**Problem**  
Given an `m x n` matrix, return all elements of the matrix in **spiral order**.

In case you don’t think about spirals that often (unless you're pondering galaxies or those satisfying snail shells), here’s what we mean:  
Start at the top-left corner and move right across the first row, then down the last column, left along the bottom row, and finally back up the first column.  
Keep spiraling inward until you’ve collected all the elements.

It’s like peeling layers off an onion… but way less tear-inducing!

---

## Example 1

**Input:**  
`matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]`

**Output:**  
`[1, 2, 3, 6, 9, 8, 7, 4, 5]`

<!-- ![Spiral Matrix Example 1 DataLemur] -->

---

## Example 2

**Input:**  
`matrix = [[1, 2, 3], [8, 9, 4], [7, 6, 5]]`

**Output:**  
`[1, 2, 3, 4, 5, 6, 7, 8, 9]`

---

## Constraints
- `m == matrix.length`
- `n == matrix[i].length`
- `1 <= m, n <= 10`
- `-100 <= matrix[i][j] <= 100`

---

## Approach

We use four boundaries to keep track of the rows and columns:
- `top`: Starting row index
- `bottom`: Ending row index
- `left`: Starting column index
- `right`: Ending column index

We iterate in the following spiral pattern:
1. Left to Right → `top++`
2. Top to Bottom → `right--`
3. Right to Left → `bottom--`
4. Bottom to Top → `left++`

We repeat this until all elements are added to the result list.

---

## Python Code

```python
def spiralOrder(matrix):
    result = []
    if not matrix:
        return result

    top, bottom = 0, len(matrix) - 1
    left, right = 0, len(matrix[0]) - 1

    while top <= bottom and left <= right:
        # Traverse from Left to Right
        for i in range(left, right + 1):
            result.append(matrix[top][i])
        top += 1

        # Traverse from Top to Bottom
        for i in range(top, bottom + 1):
            result.append(matrix[i][right])
        right -= 1

        if top <= bottom:
            # Traverse from Right to Left
            for i in range(right, left - 1, -1):
                result.append(matrix[bottom][i])
            bottom -= 1

        if left <= right:
            # Traverse from Bottom to Top
            for i in range(bottom, top - 1, -1):
                result.append(matrix[i][left])
            left += 1

    return result
