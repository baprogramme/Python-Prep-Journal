# Intersection of Two Lists

Write a function to get the **intersection** of two lists.

For example:

- **Input:**  
  `A = [1, 2, 3, 4, 5]`  
  `B = [0, 1, 3, 7]`  

- **Output:**  
  `[1, 3]`

The function should return a list containing the elements that appear in both lists.


```python


def intersection(a, b):
  c, d =set(a), set(b)
  A, B = list(c) , list(d)
  result= []
  for i in range (len(A)):
    if A[i] in B:
      result.append(A[i])
  print(result)
  return result

#OR

def intersection(a, b):
    c, d = set(a), set(b)
    result = list(c & d)  # set intersection
    print(result)
    return result

#OR

def intersection(a, b):
    result = [item for item in a if item in b]
    # Remove duplicates if needed:
    result = list(dict.fromkeys(result))
    print(result)
    return result

