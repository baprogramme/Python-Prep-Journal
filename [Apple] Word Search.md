# Word Search

## Problem Statement

Given an `m x n` grid of characters `board` and a string `word`, return **True** if `word` exists in the grid.

For the word to exist:

- You must be able to construct it from a sequence of **adjacent** cells, where adjacency is **horizontal or vertical** (not diagonal).
- The **same cell may not be used more than once**.

---

## Examples

### Example 1: Word Search DataLemur Example

```text
Input:
board = [['A', 'L', 'E', 'D'],
         ['E', 'F', 'M', 'H'],
         ['I', 'R', 'U', 'L']]
word = "LEMUR"

Output: True
```

### Example 2: Word Search Peter Example

```text
Input:
board = [['A', 'B', 'C', 'D'],
         ['P', 'E', 'T', 'H'],
         ['I', 'R', 'K', 'L']]
word = "PETER"

Output: False
```

**Explanation:** Cannot reuse the same "E".

### Example 3: Word Search Femur Example

```text
Input:
board = [['F', 'B', 'C', 'D'],
         ['E', 'M', 'G', 'H'],
         ['I', 'J', 'U', 'R']]
word = "FEMUR"

Output: False
```

**Explanation:** Cannot move diagonally from "M" to "U".

---

## Constraints

| Name                                               | Description         |
| -------------------------------------------------- | ------------------- |
| `1 ≤ m, n ≤ 6`                                     | Size of the board.  |
| `1 ≤ word.length ≤ 15`                             | Length of the word. |
| `board[i][j]` is a single uppercase English letter |                     |
| `word` is a string of uppercase English letters    |                     |

---

## Approach

Use **DFS (Depth-First Search)** + backtracking to explore the grid:

1. **Scan each cell** of the board.
2. If a cell matches the first character of the word, launch a DFS from there.
3. During DFS:
   - Mark the current cell as visited.
   - Recur for adjacent cells (up, down, left, right).
   - Restore the cell after backtracking.
4. If a path spells out the word, return True.
5. If no valid path exists, return False.

---

```python
from typing import List

def exist(board: List[List[str]], word: str) -> bool:
    rows, cols = len(board), len(board[0])

    def dfs(r, c, i):
        if i == len(word):
            return True
        if r < 0 or r >= rows or c < 0 or c >= cols:
            return False
        if board[r][c] != word[i]:
            return False

        temp, board[r][c] = board[r][c], "#"  # mark as visited

        found = (dfs(r+1, c, i+1) or
                 dfs(r-1, c, i+1) or
                 dfs(r, c+1, i+1) or
                 dfs(r, c-1, i+1))

        board[r][c] = temp  # restore cell
        return found

    for i in range(rows):
        for j in range(cols):
            if dfs(i, j, 0):
                return True

    return False
```



