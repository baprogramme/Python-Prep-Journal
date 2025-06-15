# Matrix Rotation to Match Target

Given two `n x n` binary matrices `mat` and `target`, return `true` if it is possible to make `mat` equal to `target` by rotating `mat` in **90-degree increments**, or `false` otherwise.

---

## Example #1

**Input:**  
`mat = 

[[1, 0, 1], 
        
 [0, 0, 1], 
        
[1, 0, 1]]`  
        
`target = 

[[1, 0, 1], 
           
[1, 0, 0], 
           
[1, 0, 1]]`

**Output:**  
`true`

**Explanation:**  
We can rotate `mat` 180 degrees to transform it into `target`.

### Matrix Rotation Example 1:

Original mat:

[1, 0, 1]

[0, 0, 1]

[1, 0, 1]

After 180° rotation:

[1, 0, 1]

[1, 0, 0]

[1, 0, 1]


---

## Example #2

**Input:**  
`mat = 

[[0, 1], 

[1, 0]]`  

`target = 

[[1, 1], 

[0, 0]]`

**Output:**  
`false`

**Explanation:**  
It is impossible to make `mat` equal to `target` by rotating `mat`.

Original mat:

[0, 1]

[1, 0]

Possible Rotations:
90° -> 

[1, 0]

[0, 1]

180° -> 

[0, 1]

[1, 0]

270° ->

[1, 0]

[0, 1]

None match the target:

Target:

[1, 1]

[0, 0]



``` python

def rotate(mat):
    return [list(row)[::-1] for row in zip(*mat)]

def findRotation(mat, target):
    for _ in range(4):
        if mat == target:
            return True
        mat = rotate(mat)
    return False

