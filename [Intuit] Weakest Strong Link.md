# Weakest Strong Link Problem

**Problem Statement:**  
You know that phrase, how a chain is only as strong as its weakest link?  
Imagine you had a chain-link fence, represented as a matrix. For the chain-link at position `(i, j)`, the input matrix `strength[i][j]` indicates how strong the chain is at that position (where stronger means a higher number). The numbers in the matrix are unique.

The **Weakest Strong Link** is defined as the weakest chain-link in its row **but also** the strongest link in its column.

Given a matrix `strength`, return the **weakest strong link** if it exists; otherwise, return `-1`.  
If a weakest strong link exists, it is always exactly one, and it can be proven that no other link will satisfy both conditions simultaneously.

---

### 📌 Example 1

**Input:**

strength = [[1, 2, 3],
            [4, 5, 6],
            [7, 8, 9]]
            
**Output:**
7

**Explanation:**

Row-wise minimums:

Row 1: 1

Row 2: 4

Row 3: 7

Now, check if any of these row minimums are also the maximum of their column:

Column 1: [1, 4, 7] → max = 7

Column 2: [2, 5, 8] → max = 8

Column 3: [3, 6, 9] → max = 9

7 is the minimum in its row (row 3) and the maximum in its column (column 1).

Therefore, the weakest strong link is 7.

### 📌 Example 2

**Input:**

strength = [[9, 8, 10],
            [6, 15, 4]]

**Output:**

-1


**Explanation:**

Row-wise minimums:

Row 1: 8

Row 2: 4

Check if any of these are the maximum in their column:

Column 1: [9, 6] → max = 9

Column 2: [8, 15] → max = 15

Column 3: [10, 4] → max = 10

Neither 8 nor 4 matches the maximum in their column.

No weakest strong link exists, so the result is -1.


```python

def weakest_strong_link(strength):
    n = len(strength)
    m = len(strength[0])

    for i in range(n):
        # Find the minimum in the current row
        min_row = min(strength[i])
        j = strength[i].index(min_row)  # column index of min_row

        # Check if this min_row is the maximum in its column
        col_max = max(strength[k][j] for k in range(n))

        if min_row == col_max:
            return min_row

    # If no weakest strong link is found
    return -1

