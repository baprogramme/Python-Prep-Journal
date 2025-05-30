# Factorial Formula

Given a number **n**, write a formula that returns **n!**.

In case you forgot the factorial formula:

**n! = n × (n-1) × (n-2) × ... × 2 × 1**

For example:

5! = 5 × 4 × 3 × 2 × 1 = 120
  

So we’d return **120**.

Assume **n** is a non-negative integer.


``` python
def factorial(n):
  result = 1 
  for i in range (n):
    result = result *(n-i)
  
  return result
    
  
# OR 


def factorial(n):
    if n == 0 or n == 1:
        return 1
    return n * factorial(n-1)
