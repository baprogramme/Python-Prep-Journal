# Pascal's Triangle

## Problem Statement

Given an integer `numRows`, return the first `numRows` of Pascal's triangle.

In Pascal's triangle, each number is the sum of the two numbers directly above it, as shown below.

### Pascal's Triangle

Row 0: [1]
Row 1: [1, 1]
Row 2: [1, 2, 1]
Row 3: [1, 3, 3, 1]
Row 4: [1, 4, 6, 4, 1]


## Examples

- For `numRows = 1`, you should return:


[[1]]


For numRows = 4, you should return:

[[1], [1, 1], [1, 2, 1], [1, 3, 3, 1]]


```python

def generate(numRows):
    result = []

    for i in range(numRows):
        # Start each row with '1'
        row = [1] * (i + 1)

        # Update middle elements (not the first or last) using the previous row
        for j in range(1, i):
            row[j] = result[i - 1][j - 1] + result[i - 1][j]

        result.append(row)

    return result
