# K-Radius Subarray Averages

You're given an array `nums` of `n` integers and an integer `k`.

The **k-radius average** for a subarray of `nums` centered at some index `i` is the average of all elements from indices `i - k` to `i + k` (inclusive).  
If there aren’t enough elements before or after index `i` to cover this radius, the **k-radius average is -1**.

Build and return an array `averages` of length `n`, where `averages[i]` contains the k-radius average for the subarray centered at index `i`.

Return your result **rounded to 2 decimal places**.

---

## Example 1

**Input:**  
`nums = [7, 2, 5, 12, 9, 4, 1]`, `k = 2`

**Output:**  
`[-1, -1, 7.0, 6.4, 6.2, -1, -1]`

**Explanation:**

- For `i = 0, 1, 5, 6`: there aren’t enough elements before or after, so `averages[i] = -1`.
- For `i = 2`:  
  Subarray is `[7, 2, 5, 12, 9]` →  
  Average = `(7 + 2 + 5 + 12 + 9) / 5 = 35 / 5 = 7.0`
- For `i = 3`:  
  Subarray is `[2, 5, 12, 9, 4]` →  
  Average = `(2 + 5 + 12 + 9 + 4) / 5 = 32 / 5 = 6.4`
- For `i = 4`:  
  Subarray is `[5, 12, 9, 4, 1]` →  
  Average = `(5 + 12 + 9 + 4 + 1) / 5 = 31 / 5 = 6.2`

---

## Constraints

- `n == len(nums)`
- `1 <= n <= 10^5`
- `0 <= nums[i] <= 10^5`
- `0 <= k <= (n - 1) // 2`

---


```python

def get_k_radius_averages(nums, k):
    n = len(nums)
    res = [-1] * n
    window_size = 2 * k + 1
    
    if window_size > n:
        return res
    
    window_sum = sum(nums[:window_size])
    res[k] = round(window_sum / window_size, 2)
    
    for i in range(k + 1, n - k):
        window_sum += nums[i + k] - nums[i - k - 1]
        res[i] = round(window_sum / window_size, 2)
    
    return res

